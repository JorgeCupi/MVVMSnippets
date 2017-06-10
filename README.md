# MVVMSnippets
Just a handful of snippets to accelerate the implementation of Properties, Commands, Collections and the OnPropertyChanged method
## How to add this snippets to Visual Studio?
1. Download the snippets you want to use
2. Open Visual Studio
3. Go to Tools -> Code Snippets Manager -> Add
4. Done!

## PropertyChangedEventHandler (
Use 'inpc' snippet. (File INPC.snippet)
```csharp
public event PropertyChangedEventHandler PropertyChanged;
    protected void OnPropertyChanged(string propertyName)
    {
    if (PropertyChanged != null)
      PropertyChanged(this, new PropertyChangedEventArgs(propertyName));
    }
```

## Full property supporting PropertyChanged
Use 'propx' snippet. (File INPCProp.snippet)
```csharp
   private string _PropertyName;
        public string PropertyName
        {
            get { return _PropertyName; }
            set
            {
                _PropertyName = value;
                OnPropertyChanged("PropertyName");
            }
        }
```

## Full ObservableCollection property supporting PropertyChanged
Use 'propxcol' snippet. (File INPCCol.snippet)
```csharp    
    private ObservableCollection<string> _PropertyName;
        public ObservableCollection<string> PropertyName
        {
            get { return _PropertyName; }
            set
            {
                _PropertyName = value;
                OnPropertyChanged("PropertyName");
            }
        }

        private void PropertyName_CollectionChanged(object sender, NotifyCollectionChangedEventArgs e)
        {
            OnPropertyChanged("PropertyName");
        }
        //ToDo:
        //Insert this on your constructor:
        PropertyName = new ObservableCollection<string>();
        PropertyName.CollectionChanged += PropertyName_CollectionChanged;
```

## Command implementation
Use 'xcom' snippet. (File INPCCommand.snippet)
```csharp 
    public ICommand MethodNameCommand { get; set; }
        public void MethodName()	
        {
            // Copy & Paste this into your Constructor:
            MethodNameCommand = new Command(MethodName);

            // ToDo: Your work goes here:
        }
```
