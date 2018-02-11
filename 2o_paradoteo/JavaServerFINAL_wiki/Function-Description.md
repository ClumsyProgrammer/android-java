## Πίνακας Μεθόδων

Λίστα μεθόδων ανά κλάση

- JavaServer
  * sample
      - DataBases  
        + Records  
            * **Record**
                  - **String get_record_id()** -> Επιστρέφει τον αναγνωριστικό αριθμό της εγγραφής.
                  - **void set_record_id(String id)** -> Θέτει τον αναγνωριστικό αριθμό της εγγραφής.
                  - **String get_terminal_id()** -> Επιστρέφει την ταυτότητα του τερματικού αυτής της εγγραφής.
                  - **String get_sensor_id()** -> Επιστρέφει την ταυτότητα του αισθητήρα αυτής της εγγραφής.
                  - **void set_sensor_id(String id)** -> Θέτει την ταυτ'οτητα αισθητήρα αυτής της εγγραφής.
                  - **String get_sensor_value()** -> Επιστρέφει την τιμή του αισθητήρα αυτής της εγγραφής.
                  - **String get_danger_status()** -> Επιστρέφει την κατάσταση κινδύνου αυτής της εγγραφής. 
                  - **void set_danger_status(String value)** -> Θέτει την κατάσταση κινδύνου αυτής της εγγραφής.
                  - **String get_timestamp()** -> Επιστρέφει την χρονοσφραγίδα της εγγραφής.
                  - **String get_position_x()** -> Επιστρέφει τη συντεταγμένη μήκους της εγγραφής.
                  - **String get_position_y()** -> Επιστρεφει τη συντεταγμένη πλάτους της εγγραφής.

            * **RecordBean**
                  - **public RecordBean()** -> Δημιουργεί αντικείμενο τύπου RecordBean και επιχειρεί σύνδεση με τη βάση δεδομένων.
                  - **public Record create(Record p)** -> Εισάγει την εγγραφή p στη βάση δεδομένων.

            * **SortRecords**  
                  - **SortRecords(Record rec)** -> Δημιουργεί αντικείμενο τύπου SortRecords και ταξινομεί τη δοσμένη εγγραφή ως προς την ταυτότητα του αισθητήρα. Αν η εγγραφή παρουσιάζει επικείμενο  κίνδυνο, η set_record εκκινεί διαδικασία εισαγωγής στη βάση δεδομένων. 
                  - **private void set_record(Record rec)** -> Το αντίστοιχο τερματικό ενημερώνεται μέσω terminal_tree, ανασύρεται από τα storred_settings  ο αριθμός των τρεχουσσών εγγραφών, υπολογίζεται ο τύπος κινδύνου (απλός ή επιβεβαιωμένος) και η RecordBean εισάγει την εγγραφή στη βάση δεδομένων. 
                  - **public static Record extract_record(String in_mess)** -> Δημιουργεί μια νέα εγγραφή, διαχωρίζοντας τη δοσμένη γραμματοσειρά.

        + Terminals
            - **DangerDetector**
                  * **private DangerDetector()** -> Δημιουργεί αντικείμενο τύπου DangerDetector.
                  * **public static DangerDetector getInstance()** -> Επιστρέφει υπάρχον στιγμιότυπο του DangerDetector, διαφορετικά δημιουργεί νέο.
                  * **public String CheckTerminal(String uuid)** -> Επιστρέφει τον τύπο κινδύνου που αντιμετωπίζει ένα τερματικό (safe, simple, verified).

            - **Node**
                  + **public Node(Node parent)** -> Δημιουργεί νέο κόμβο με γονιό τον parent.
                  + **public String getId()** -> Επιστρέφει την ταυτότητα ενός κόμβου.
                  + **public void setId(String id)** -> Θέτει την ταυτότητα ενός κόμβου.
                  + **public List<Node> getChildren()** -> Επιστρέφει λίστα κόμβων με τα παιδιά του κόμβου.
                  + **public Node getParent()** -> Επιστρέφει τον κόμβο-γονιό ενός κόμβου.
                  + **public static Node addChild(Node parent, String id)** -> Επιστρέφει ένα νέο κόμβο αφού τον δημιουργήσει, με το δοσμένο γονιό και την αντίστοιχη ταυτότητα.
                  + **public void removeChild()** -> απομακρύνει τον κόμβο από το γονιό του.

            - **TerminalTree**  
                + **private TerminalTree()** -> Δημιουργεί αντικείμενο τύπου TerminalTree.
                + **public static TerminalTree getInstance()** -> Επιστρέφει υπάρχον στιγμιότυπο του TerminalTree, διαφορετικά δημιουργεί νέο.
                + **public void clear_tree()** -> Στρέφει τη ρίζα του δέντρου σε null.
                + **public void AddTerminal(String uuid)** -> Προσθέτει τερματικό με ταυτότητα uuid στο δέντρο αν δεν υπάρχει ήδη και ο subscriber εγγράφεται στο κατάλληλο topic .
                + **public void RemoveTerminal(String uuid)** -> Απομακρύνει το τερματικό με ταυτότητα uuid από το δέντρο και ο subscriber απεγγράφεται από το αντίστοιχο topic.
                + **public void SubscribeToAllTerminals()** -> Ο subscriber εγγράφεται σε κατάλληλο topic για κάθε τερματικό που υπάρχει μέσα στο δέντρο.
                + **public ObservableList<String> TerminalsAvailable()** -> Επιστρέφει λίστα με τισ ταυτότητες όλων των διαθέσιμων τερματικών.
                + **public Node GetTerminal(String uuid)** -> Επιστρέφει τον κόμβο με ταυτότητα uuid.
                + **public void AddSensor(String uuid, String sensor_id)** -> Προσθέτει κόμβο με ταυτότητα sensor_id σε γονιό με ταυτότητα uuid.
                + **public Node GetSensor(String uuid,String sensor_id)** -> Επιστρέφει τον κόμβο με ταυτότητα sensor_id και γονιό με ταυτότητα uuid. 
                + **public void AddDanger(String uuid, String sensor_id, String danger)** -> Προσθέτει κόμβο με ταυτότητα danger, σε γονιό με ταυτότητα sensor_id του οποίου ο γονιός έχει ταυτότητα uuid.
                + **public void SetDanger(String uuid,String sensor_id, String danger)** -> Θέτει την ταυτότητα σε κόμβο με γονιό με ταυτότητα sensor_id του οποίου ο γονιός έχει ταυτότητα uuid.
                + **public Boolean IsTerminalInDanger(String uuid)** -> Επιστρέφει true σε περίπτωση που κάποιο από τα φύλλα του τερματικού uuid είναι ίσο με "TRUE".  Διαφορετικά επιστρέφει false.
                + **public Boolean OtherTerminalsInDanger(String uuid)** -> Επιστρέφει true σε περίπτωση που κάποιο από τα φύλλα τερματικού με ταυτότητα διάφορη του uuid είναι ίσο με "TRUE".  Διαφορετικά επιστρέφει false.

        + **DataBaseAgent**
              - **private DataBaseAgent()** -> Δημειουργεί αντικείμενο τύπου DataBaseAgent και συνδέεται στη βάση δεδομένων.
              - **public static DataBaseAgent getInstance()** -> Επιστρέφει στιγμιότυπο του DataBaseAgent. Αν δεν υπάρχει καλείται o constructor.
              - **public ObservableList<ObservableList<String>> BuildData()** -> Επιστρέφει σε λίστα όλο το περιεχόμενο της βάσης δεδομένων.
              - **public ObservableList<ObservableList<String>> SearchData(String value)** -> Επιστρέφει σε λίστα το περιεχόμενο της βάσης δεδομένων που αντιστοιχεί στα κριτήρια αναζήτησης value.
              - **public void BuildTable(TableView table)** -> Μορφοποιεί το table και τις στήλες του σύμφωνα με τις ιδιότητες της βάσης δεδομένων.
              - **public void ClearData()** -> Απομακρύνει όλες τις εγγραφές από τη βάση δεδομένων.
              - **public void TerminalsAvailable(TableView table)** -> Γεμίζει το table με τις ταυτότητες των διαθέσιμων τερματικών.
              - **public void TerminalsSetColumns(TableView table)** -> Μορφοποίηση στηλών του table για τα διαθέσιμα τερματικά.

      - MQTT  
        - **ConnectivityHandler**
              * **public ConnectivityHandler()** -> Δημιουργεί αντικείμενο τύπου ConnectivityHandler, το οποίο εκκινεί τη διαδικασία σύνδεσης στον mqtt broker και τη βάση δεδομένων σε νέα thread.
              * **static void print_exception(MqttException me2)** -> Εκτυπώνει στην κονσόλα τα αίτια μιας πιθανής Mqtt εξαίρεσης. 

        - **MessageSort**  
          * **static void sorting(String in_mess)** -> Διαχωρίζει τα εισερχόμενα μηνύματα βάσει θέματος και καλεί τις κατάλληλες κλάσεις, είτε για διαθεσιμότητα τερματικού, είτε για δημιουργία νέας εγγραφής. 

        - **Mqtt_publisher**
              * **private Mqtt_publisher()** -> Δημιουργεί αντικείμενο τύπου Mqtt_publisher, φτιάχνοντας ένα νέο πελάτη.
              * **public static Mqtt_publisher getInstance()** -> Επιστρέφει υπάρχον στιγμιότυπο του Mqtt_publisher, διαφορετικά δημειουργεί νέο.
              * **private void create_client()** -> Φτιάχνει ένα νέο πελάτη με τις ενσωματωμένες στην εφαρμογή ιδιότητες.
              * **public void publish(String topic, String content)** -> Ο πελάτης δημοσιεύει μήνυμα με θέμα topic και περιεχόμενο content.
              * **public void disconnect()** -> Ο πελάτης αποσυνδέεται απο τον broker.
              * **public void terminate(ObservableList<String> terms)** -> Ενημερώνονται όλα τα τερματικά για το επικείμενο κλείσιμο της εφαρμογής.

        - **Mqtt_subscriber**
            - **private Mqtt_subscriber()** -> Δημιουργεί αντικείμενο τύπου Mqtt_subscriber, φτιάχνοντας ένα νέο πελάτη.
            - **public static Mqtt_subscriber getInstance()** -> Επιστρέφει υπάρχον στιγμιότυπο του Mqtt_subscriber, διαφορετικά δημειουργεί νέο.
            - **private void create_client()** -> Φτιάχνει ένα νέο πελάτη με τις ενσωματωμένες στην εφαρμογή ιδιότητες.
            - **void subscribe_Availability()** -> Ο πελάτης εγγράφεται στο θέμα "Availability".
            - **public void subscribe_Terminal(String add_uuid)** -> Ο πελάτης εγγράφεται στο θέμα <uuid>.
            - **public void unsubscribe_Terminal(String drop_uuid)** -> Ο πελάτης απεγγράφεται απο το θέμα <uuid>.
            - **public void disconnect()** -> Ο πελάτης αποσυνδέεται απο τον broker.
            - **public void connectionLost(Throwable cause)** -> Σε περίπτωση προβλήματος στη σύνδεση εκτυπώνεται το αντίστοιχο μήνυμα στην κονσόλα.
            - **public void deliveryComplete(IMqttDeliveryToken token)** -> Δεν χρησιμοποιείται.
            - **public void messageArrived(String topic, MqttMessage message) throws MqttException** -> Η MessageSort αναλαμβάνει να κατηγοριοποιήσει το εισερχόμενο μήνυμα.

      - SceneControl
        - **GeneralLayout**
            - **GeneralLayout()** -> Δημιουργεί ένα νέο αντικείμενο τύπου GeneralLayout και αρχικοποιεί τα μέλη της κλάσης.
            - **private Node createPage(int pageIndex)** -> Φτιάχνει το tableview της σελίδας pageIndex της σελιδοποίησης, γεμίζοντας το με τα στοιχεία υπολίστας της λίστας με όλες τις εγγραφές που έχει ζητήσει ο χρήστης.
            - **private Pane SearchDataBase()** -> Πλαίσιο με τα γραφικά στοιχεία για την αναζήτηση της βάσης δεδομένων.
            - **Pane DataTab()** -> Δημιουργεί τα γραφικά στοιχεία της καρτέλας δεδομένων.
            - **Pane SettingsTab()** -> Δημιουργεί τα γραφικά στοιχεία της καρτέλας ρυθμίσεων.
            - **private Pane Sliders_Thresholds()** -> Πλαίσιο για τις κυλιόμενες μπάρες των κατωφλίων με τους αντίστοιχους listeners.
            - **private Pane Sliders_Time_Intervals()** -> Πλαίσιο για τις κυλιόμενες μπάρες των χρονικών διαστημάτων με τους αντίστοιχους listeners.

        - **SceneCreator**  
            - **public SceneCreator(Stage primaryStage)** -> Δημιουργεί το γραφικό περιβάλλον της εφαρμογής.
      - **ExitHandler**
          - **ExitHandler()** -> Διαχειρίζεται το κλείσιμο της εφαρμογής: Ειδοποιεί όλα τα διαθέσιμα τερματικά και κλείνει τις συνδέσεις με τον broker. 
      - **Main**
          - **public static void main(String[] args)** ->  Εκκινεί την εφαρμογή.
          - **public void start(Stage primaryStage)** -> Δημιουργεί νέα νήμματα για κάθε συστατικό της εφαρμογής και ορίζει την πολιτική τερεματισμού.

      - **StoredSettings**
          - **private StoredSettings()** -> Δημιουργεί αντικείμενο τύπου StoredSettings.
          - **public static StoredSettings getInstance()** -> Επιστρέφει το υπάρχον στιγμιότυπο του StoredSettings, διαφορετικά δημιουργεί νέο. 
          - **public void saveData(String key, String value)** -> Αποθηκεύει το ζεύγος key - value.
          - **public String getData(String key)** -> Επιστρέφει την τιμή της μεταβλητής key.



