# keyboarder
iOS Keyboard handler for view 

Sample usage

class SampleViewController: UIViewController, UITextFieldDelegate, KeyboarderDelegate
{
    @IBOutlet weak var textName: UITextField!
    @IBOutlet weak var textPhone: UITextField!
    @IBOutlet weak var scrollView: UIScrollView!

    var keyboarder: Keyboarder!;
    
    override func viewDidLoad()
    {
        super.viewDidLoad()

        keyboarder = Keyboarder(self.view, scrollView, delegate: self);

        textName.delegate = self;
        textPhone.delegate = self;
    }
    
    
    override func viewWillAppear(_ animated: Bool)
    {
        super.viewWillAppear(animated)
        
        keyboarder.viewWillAppear();
    }
    
    override func viewWillDisappear(_ animated: Bool)
    {
        super.viewWillDisappear(animated)
        
        keyboarder.viewWillDisappear();
    }
    
    //MARK: - UITextFieldDelegate
    public func textFieldDidBeginEditing(_ textField: UITextField)
    {
        keyboarder.inputBegin(textField)
    }
    
    public func textFieldDidEndEditing(_ textField: UITextField)
    {
        keyboarder.inputEnd(textField)
    }
    
    //MARK: - KeyboarderDelegate
    func keyboarderResign(_ keyboarder: Keyboarder!)
    {
        self.textName.resignFirstResponder();
        self.textPhone.resignFirstResponder();
    }   
}
