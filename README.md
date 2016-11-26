# MVVMSnippets
Just a handful of snippets to accelerate the implementation of Properties, Commands, Collections and the OnPropertyChanged method

## PropertyChangedEventHandler 
```csharp
public event PropertyChangedEventHandler PropertyChanged;
    protected void OnPropertyChanged(string propertyName)
    {
    if (PropertyChanged != null)
      PropertyChanged(this, new PropertyChangedEventArgs(propertyName));
    }
```

## Full property supporting PropertyChanged
```csharp
   private string _myVar;
        public string myProp
        {
            get { return _myVar; }
            set
            {
                _myVar = value;
                OnPropertyChanged("myProp");
            }
        }
```

## Full ObservableCollection property supporting PropertyChanged
```csharp    
    private ObservableCollection<string> _myVar;
        public ObservableCollection<string> myProp
        {
            get { return _myVar; }
            set
            {
                _myVar = value;
                OnPropertyChanged("myProp");
            }
        }

        private void myProp_CollectionChanged(object sender, NotifyCollectionChangedEventArgs e)
        {
            OnPropertyChanged("myProp");
        }
        //ToDo:
        //Insert this on your constructor:
        myProp = new ObservableCollection<string>();
        myProp.CollectionChanged += myProp_CollectionChanged;
```

## Command implementation
```csharp 
    public ICommand myMethodCommand { get; set; }
        public void myMethod()	
        {
            // Copy & Paste this into your Constructor:
            myMethodCommand = new Command(myMethod);

            // ToDo: Your work goes here:
        }
```
