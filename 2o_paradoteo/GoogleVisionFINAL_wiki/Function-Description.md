## Πίνακας Μεθόδων

Λίστα μεθόδων ανά κλάση
- GoogleVision
  - Activities
        - **MainActivity**
            - **private final BroadcastReceiver** -> Λήψη ειδοποιήσεων από στοιχεία του συστήματος ή άλλα κομμάτια της εφαρμογής και οι αντίστοιχες δράσεις.
            - **private void set_filters()** -> Φίλτρα των ειδοποιήσεων που λαμβάνει η συγκεκριμένη κλάση.
            - **private void set_frag_view()** -> Απόφαση εμφάνισης ή μη των διάφορων fragments ανάλογα με τη διαθεσιμότητα των αντίστοιχων αισθητήρων.
            - **public void onCreate(Bundle savedInstanceState)** -> Ανασύρει το προηγούμενο στιγμιότυπο αν υπάρχει, διαφορετικά φτιάχνει καινούριο. Αρχικοποίηση των μελών της κλάσης και εκκίνηση των υπηρεσιών, listeners για την αλληλεπίδραση των γραφικών στοιχείων με το χρήστη.
            - **protected void onDestroy()** -> αποδεύσμευση του BroadcastReceiver.
            - **public void onBackPressed()** -> Σύνολο δράσεων σε περίπτωση που πατηθεί το "προς τα πίσω" κουμπί.
        - **OnlineSettingsFragment**
            - **public OnlineSettingsFragment()** -> άδειος constructor.
            - **public void onCreate(Bundle savedInstanceState)** -> Ανάσυρση στιγμιοτύπου.
            - **public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)**  -> Δημιουργεία του γραφικού στοιχείου και ανάθεση listeners.
            - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
            - **public void onDetach()** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
        - **SettingsActivity**
            - **private final BroadcastReceiver** -> Λήψη ειδοποιήσεων από στοιχεία του συστήματος ή άλλα κομμάτια της εφαρμογής και οι αντίστοιχες δράσεις.
            - **private void set_frag_view()** -> Απόφαση εμφάνισης ή μη των διάφορων fragments ανάλογα με τη διαθεσιμότητα των αντίστοιχων αισθητήρων.
            - **private void set_filters()** -> Φίλτρα των ειδοποιήσεων που λαμβάνει η συγκεκριμένη κλάση.
            - **protected void onCreate(Bundle savedInstanceState)** -> Ανασύρει το προηγούμενο στιγμιότυπο αν υπάρχει, διαφορετικά φτιάχνει καινούριο. Εμφάνιση των γραφικών στοιχείων.
  - CollisionTools
        - **Collision_Settings**
            - **public static Collision_Settings getInstance(Context context)** -> Επιστρέφει το υπάρχον στιγμιότυπο του Collision_Settings, διαφορετικά κατασκευάζει καινούριο. 
            - **private Collision_Settings(Context context)** -> Δημιουργεί ένα αντικείμενο τύπου, ανασύρει τα shared preferences και θέτει ορισμένες  default τιμές αν δεν έχουν οριστεί άλλες από το χρήστη.
            - **public void saveData(String key, String value)** -> Αποθηκέυει το ζεύγος key - value.
            - **public String getData(String key)** -> Επιστρέφει την τιμή του πεδίου key.
        - **CollisionNotifier**
            - **private void check_danger(Context context)** -> Υπολογίζει τον κίνδυνο για κάθε αισθητήρα και τελικά τον καθολικό κίνδυνο για το τερματικό σε εκτός σύνδεσης λειτουργεία. 
            - **private final BroadcastReceiver** -> Τίθενται οι απαραίτητοι Broadcast Receivers ούτως ώστε να ειδοποιείται η κλάση σε κάθε αλλαγή και να υπολογίζεται εκ νέου ο τρέχων κίνδυνος. 
            - **CollisionNotifier(Context context)** -> Συνάρτηση κατασκευής. Επιπλέον ορίζονται τα κατάλληλα φίλτρα για τις ειδοποιήσεις.
        - **OfflineNotify**
            - **private void post_alert()** -> Παράγει οπτική και ηχητική ειδοποίηση σύμφωνα με την τιμή του GLOBAL_DANGER σε offline κατάσταση.
            - **public OfflineNotify(final Context context)** -> Συνάρτηση κατασκευής. Επιπλέον ορίζει το περιεχόμενο του toast message στο main thread.
        - **OnlineNotify**
            - **private void post_alert()** -> Παράγει οπτική και ηχητική ειδοποίηση σύμφωνα με την τιμή του REMOTE_DANGER σε online κατάσταση.
            - **OnlineNotify(final Context context)** -> Συνάρτηση κατασκευής. Επιπλέον ορίζει το περιεχόμενο του toast message στο main thread.
        - **SensorService**
            - **public SensorService()** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
            - **public void onCreate()** -> Παράγει log μήνυμα για την επίδειξη της έναρξης της υπηρεσίας.
            - **public int onStartCommand(final Intent intent, int flags, int startId)** -> Δημειουργεί νέa thread για κάθε σένσορα, καθώς επίσης και για τις κλάσης ελέγχου κινδύνου, ειδοποίησης και χειριστή συνδεσιμότητας.
            - **public IBinder onBind(Intent intent)** -> Η υπηρεσία δεν προσάπτεται σε καμία activity.
            - **public void onDestroy()** -> Παράγει απλή log ειδοποίηση.
  - Connectivity
        - **ConnectivityHandler**
            - **public static ConnectivityHandler getInstance(Context context)** -> Επιστρέφει υπάρχον στιγμιότυπο του ConnectivityHandler, διαφορετικά δημιουργεί νεό. 
            - **private ConnectivityHandler(Context context)** -> Δημιουργεί ένα νέο αντικείμενο τύπου ConnectivityHandler, αναγνωρίζει τις δυνατότητες σύνδεσης της συσκευής, καλεί στιγμιότυπα των publisher και subscriber και επιχειρεί σύνδεση σε νέο thread.
            - **private static void get_uuid(Context context)** -> Αποθηκεύει την uuid της συσκευής στα ConnectivitySettings. 
            - **public void publish_string(String key, String value)** -> Ελέγχει τη συνδεσιμότητα της συσκευής και, αν το string προς δημοσίευση ανήκει σε τιμή αισθητήρα, το αποστέλει μέσω publisher.
            - **public void isNetworkConnected(Context context)** -> Ελέγχει τη δυνατότητα σύνδεσης της συσκευής στο Internet και την παρουσία GPS.
            - **private void update_clients()** -> Καλεί pub/sub να απομακρύνουν το παλαιό αντικείμενο client, και να δημιουργήσουν νέο με τις καινούριες ρυθμίσεις του χρήστη, και επιχειρεί σύνδεση σε νέο thread.
            - **public void switch_off()** -> Μετάβαση σε offline λειτουργεία: Καλεί pub/sub να αποσυνδεθούν αφού πρώτα δημοσιευθεί η αλλαγή κατάστασης.
            - **public void switch_on()** -> Μετάβαση σε online λειτουργεία: Καλεί pub/sub να συνδεθούν, να δημοσιευθεί η αλλαγή κατάστασης και να εγγραφεί το τερματικό στα κατάλληλα θέματα.
            - **static void print_exception(MqttException me2)** -> Εκτυπώνει τα αίτια μιας Mqtt εξαίρερσης.
            - **private final BroadcastReceiver** -> Υποδοχείς για τη λήψη ειδοποιήσεων.
            - **private void set_filters(Context context)** -> Φίλτρα για τη λήψη ειδοποιήσεων.
        - **ConnectivitySettings**
            - **public static ConnectivitySettings getInstance(Context context)** -> Επιστρέφει το υπάρχον στιγμιότυπο του ConnectivitySettings, διαφορετικά κατασκευάζει καινούριο.
            - **private ConnectivitySettings(Context context)** -> Δημιουργεί ένα αντικείμενο τύπου ConnectivitySettings, ανασύρει τα shared preferences και θέτει ορισμένες  default τιμές αν δεν έχουν οριστεί άλλες από το χρήστη.
            - **public void saveData(String key, String value)** -> Αποθηκέυει το ζεύγος key - value.
            - **public String getData(String key)** -> Επιστρέφει την τιμή του πεδίου key.
        - **Mqtt_publisher**
            - **private Mqtt_publisher()** -> Δημιουργεί ένα νέο αντικείμενο τύπου Mqtt_publisher και ένα νέο client.
            - **public static Mqtt_publisher getInstance(Context context)** -> Επιστρέφει υπάρχον στιγμιότυπο του Mqtt_publisher, διαφορετικά δημιουργεί νεό. 
            - **private void create_client()** -> Δημιουργεί ένα νέο πελάτη με τις αποθηκευμένες ρυθμίσεις. 
            - **public void update_client()** -> Δημιουργεί ένα νέο πελάτη με τις νέες ρυθμίσεις και επιχειρεί σύνδεση. 
            - **public void connect()** -> Eάν ο πελάτης δεν είναι συνδεδεμένος, επιχειρεί νέα σύνδεση με τον broker.
            - **public void publish(String topic, String content)** -> Δημιουργεί ένα νέο MqttMessage. Αν ο πελάτης είναι συνδεδεμένος το αποστέλει. 
            - **public void disconnect()** -> Αν ο πελάτης είναι συνδεδεμένος, αποσυνδέεται.
        - **Mqtt_subscriber**
            - **Mqtt_subscriber()** ->  -> Δημιουργεί ένα νέο αντικείμενο τύπου Mqtt_subscriber και ένα νέο client.
            - **public static Mqtt_subscriber getInstance(Context context)** -> Επιστρέφει υπάρχον στιγμιότυπο του Mqtt_subscriber, διαφορετικά δημιουργεί νεό. 
            - **private void create_client()** -> Δημιουργεί ένα νέο πελάτη με τις αποθηκευμένες ρυθμίσεις. 
            - **public void update_client()**  -> Δημιουργεί ένα νέο πελάτη με τις νέες ρυθμίσεις και επιχειρεί σύνδεση. 
            - **public void connect()** -> Eάν ο πελάτης δεν είναι συνδεδεμένος, επιχειρεί νέα σύνδεση με τον broker.
            - **public void subscribe(String topic)** -> Ο πελάτης εγγράφεται στο θέμα topic.
            - **public void UnSubscribe(String topic)** -> Ο πελάτης απεγγράφεται από το θέμα topic.
            - **public void disconnect()** -> Εάν ο πελάτης είναι συνδεδεμένος, αποσυνδέεται.
            - **public void connectionLost(Throwable cause)** -> Ενημερώνει για την απώλεια σύνδεσης με μήνυμα στην κονσόλα.
            - **public void deliveryComplete(IMqttDeliveryToken token)** -> Δεν χρησιμοποιείται.
            - **public void messageArrived(String topic, MqttMessage message) throws Exception** -> Κατηγοριοποιεί τα εισερχόμενα μηνύματα βάσει θέματος και περιεχομένου και αποθηκεύει το περιεχόμενο στα κατάλληλα πεδία.
  - GoogleVision
        - **NewCamera**
            - **public NewCamera(Context context)** -> Εάν υπάρχει διαθέσιμη κάμερα και σύνδεση σε δίκτυο, δημιουργεί ένα νέο αντικείμενο τύπου NewCamera. 
            - **public void take_picture()** -> Τραβάει φωτογραφία.
            - **public boolean isNetworkConnected(Context context)** -> Ελέγχει τη συνδεσιμότητα με το δίκτυο.
            - **protected CameraDevice.StateCallback** -> Ανοίγει την κάμερα και τη θέτει σε αναμονή.
            - **protected CameraCaptureSession.StateCallback** -> Παραμετροποίηση της συνεδρίας λήψης στιγμιοτύπων.
            - **protected ImageReader.OnImageAvailableListener** -> Ειδοποιείται για τη διαθεσιμότητα νέας φωτογραφίας, παίρνει την τελευταία και τη προωθεί για επεξεργασία.
            - **public boolean readyCamera(Context context)** -> Επιστρέφει true ή false ανάλογα με τη διαθεσιμότητα της κάμερας. 
            - **public String getCamera(CameraManager manager)** -> Ζητά από το σύστημα πρόσβαση στην μπροστινή κάμερα.
            - **public void actOnReadyCameraDevice()** -> Δημιουργεί νέα συνεδρία λήψη στιγμιοτύπων. 
            - **public void onDestroy()** -> Κλείνει τη συνεδρία λήψης στιγμιοτύπων. 
            - **private void processImage(android.media.Image image)** -> Αποθηκεύει τη φωτογραφία και υποβάλλει το uri της στα Connectivity Settings.
            - **private static File getOutputMediaFile(int type)** -> Δημιουργεί όνομα για το αρχείο φωτογραφίας και εξασφαλίζει την πρόσβαση στο φάκελλο "MyCameraApp".
            - **protected CaptureRequest createCaptureRequest()** -> Δημιουργεί εντολή λήψης φωτογραφίας.
        - **OldCamera**
            - **public OldCamera(Context context)** -> Σε περίπτωση διαθεσιμότητας δικτύου και κάμερας υποβάλλει θετική σημαία στα Connectivity Settings.
            - **private Boolean getOldCamera(Context context)** -> Ελέγχει τη διαθεσιμότητα της κάμερας και αποκτά πρόσβαση σε αυτή.
            - **public boolean isNetworkConnected(Context context)** -> Ελέγχει τη διαθεσιμότητα του δικτύου.
            - **public void take_picture()** -> Τραβάει φωτογραφία.
            - **private static Uri getOutputMediaFileUri(int type)** -> Επιστρέφει  το uri του αρχείου έπειτα από κλήση της getOutputMediaFile(int type).
            - **private static File getOutputMediaFile(int type)** -> Δημιουργεί όνομα για το αρχείο φωτογραφίας και εξασφαλίζει την πρόσβαση στο φάκελλο "MyCameraApp".
            - **private Camera.PictureCallback**  -> Αποθηκεύει τη φωτογραφία και υποβάλλει το uri της στα Connectivity Settings.
            - **public static Camera getCameraInstance()** -> Επιστρέφει το αντικείμενο κάμερας που ζητήθηκε.
            - **private boolean checkCameraHardware(Context context)** -> Ελέγχει τη διαθεσιμότητα της κάμερας.
        - **PackageManagerUtils**
            - **public static String getSignature(@NonNull PackageManager pm, @NonNull String packageName)** -> Ανασύρει την SHA1 υπογραφή
            - **private static String signatureDigest(Signature sig)** -> Μορφοποιεί κατάλληλα την SHA1 υπογραφή.
        - **PermissionUtils** 
            - **public static boolean requestPermission(Activity activity, int requestCode, String... permissions)** -> Ζητά αδειοδότηση.
            - **public static boolean permissionGranted(int requestCode, int permissionCode, int[] grantResults)** -> Επιστρέφει την απάντηση του συστήματος.
        - **VisionService**
            - **public VisionService()** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
            - **public void onCreate()** -> Παράγει log μήνυμα για την επίδειξη της έναρξης της υπηρεσίας.
            - **public int onStartCommand(final Intent intent, int flags, int startId)** -> Δημιουργεί μια νεα κάμερα ανάλογα με την έκδοση του λειτουργικού συστήματος, αρχικοποιεί ένα text-to-speach αντικείμενο και θέτει τα κατάλληλα φίλτρα ούτως ώστε σε περίπτωση κινδύνου, είτε online είτε offline, να τραβηχτεί φωτογραφία.
            - **private void take_picture()** -> Αναθέτει στην κατάλληλη κάμερα να τραβήξει φωτογραφία.
            - **public void uploadImage(Uri uri)** -> Σμίκρυνση της φωτογραφίας και αποστολή στο cloud, μόλις υποβληθεί στα Connectivity Settings νέο uri.
            - **private void callCloudVision(final Bitmap bitmap) throws IOException** -> Αποστολή του αιτήματος ανάλυσης της φωτογραφίας, επεξεργασία της απάντησης και μετατροπή σε φωνητική ειδοποίηση.
            - **public Bitmap scaleBitmapDown(Bitmap bitmap, int maxDimension)** -> Σμίκρυνση της φωτογραφίας.
            - **private String convertResponseToString(BatchAnnotateImagesResponse response)** -> Μετατρέπει την απάντηση του Cloud σε ένα απλό String.
            - **public IBinder onBind(Intent intent)** -> Η υπηρεσία δεν προσάπτεται σε καμία activity.
            - **public void onDestroy()** -> Παράγει απλή log ειδοποίηση.
  - Sensors
        - AcceleratorSensorTools
            - **Accelerator_Sensor**
                - **private String check_accelerator(Double reading, Double threshold, Context context)** -> Υπολογίζει την κατάσταση κινδύνου βάσει τις παρούσας τιμής του αισθητήρα και του αντίστοιχου κατωφλίου.
                - **public Accelerator_Sensor(final Context context)** -> Θέτει ερώτηση στο σύστημα για τη διαθεσιμότητα του αισθητήρα. Σε περίπτωση θετικής απάντησης προσάπτονται οι κατάλληλοι listeners. Επίσης τοποθετούνται τα κατάλληλα φίλτρα για ενημέρωση αλλαγής κατωφλίων.
            - **AcceleratorFragment**
                - **public AcceleratorFragment()** -> Αδειος constructor.
                - **public void onCreate(Bundle savedInstanceState)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public View onCreateView(LayoutInflater inflater, ViewGroup container,Bundle savedInstanceState)** -> Ορίζει τα γραφικά στοιχεία για την παρουσίαση των τιμών που επιστρεφει ο αισθητήρας.
                - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public void onDetach()** -> Απελευθέρωση Broadcast Receiver.
            - **SetAcceleratorFragment**
                - **public SetAcceleratorFragment()** -> Αδειος constructor.
                - **public void onCreate(Bundle savedInstanceState)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)** -> Ορίζει τα γραφικά στοιχεία για την παρουσίαση και ρύθμιση των κατωφλίων του αισθητήρα.
                - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public void onDetach()** -> Απελευθέρωση Broadcast Receiver.
        - GPSTools
            - **GPS_Sensor**
                - **private String check_gps(Double reading_X, Double threshold_X_a,Double threshold_X_b,Double reading_Y, Double threshold_Y_a,Double threshold_Y_b, Context context)** -> Υπολογίζει την κατάσταση κινδύνου βάσει τις παρούσας τιμής του αισθητήρα και του αντίστοιχου κατωφλίου.
                - **public GPS_Sensor(final Context context)** -> Θέτει ερώτηση στο σύστημα για τη διαθεσιμότητα του αισθητήρα. Σε περίπτωση θετικής απάντησης προσάπτονται οι κατάλληλοι listeners. Επίσης τοποθετούνται τα κατάλληλα φίλτρα για ενημέρωση αλλαγής κατωφλίων.
            - **GPSFragment**
                - **public GPSFragment()** -> Αδειος constructor.
                - **public void onCreate(Bundle savedInstanceState)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)** -> Ορίζει τα γραφικά στοιχεία για την παρουσίαση των τιμών που επιστρεφει ο αισθητήρας.
                - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public void onDetach()** -> Απελευθέρωση Broadcast Receiver.
            - **SetGPSFragment**
                - **public SetGPSFragment()** -> Αδειος constructor.
                - **public void onCreate(Bundle savedInstanceState)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)** -> Ορίζει τα γραφικά στοιχεία για την παρουσίαση και ρύθμιση των κατωφλίων του αισθητήρα.
                - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public void onDetach()** -> Απελευθέρωση Broadcast Receiver.
        - GyroscopeSensorTools
            - **Gyroscope_Sensor**
                - **private String check_gyroscope(Double reading, Double threshold, Context context)** -> Υπολογίζει την κατάσταση κινδύνου βάσει τις παρούσας τιμής του αισθητήρα και του αντίστοιχου κατωφλίου.
                - **public  Gyroscope_Sensor(final Context context)** -> Θέτει ερώτηση στο σύστημα για τη διαθεσιμότητα του αισθητήρα. Σε περίπτωση θετικής απάντησης προσάπτονται οι κατάλληλοι listeners. Επίσης τοποθετούνται τα κατάλληλα φίλτρα για ενημέρωση αλλαγής κατωφλίων.
            - **GyroscopeFragment**
                - **public GyroscopeFragment()** -> Αδειος constructor.
                - **public void onCreate(Bundle savedInstanceState)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public View onCreateView(LayoutInflater inflater, final ViewGroup container, Bundle savedInstanceState)** -> Ορίζει τα γραφικά στοιχεία για την παρουσίαση των τιμών που επιστρεφει ο αισθητήρας.
                - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public void onDetach()** -> Απελευθέρωση Broadcast Receiver.
            - **SetGyroscopeFragment**
                - **public SetGyroscopeFragment()** -> Αδειος constructor.
                - **public void onCreate(Bundle savedInstanceState)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)**  -> Ορίζει τα γραφικά στοιχεία για την παρουσίαση και ρύθμιση των κατωφλίων του αισθητήρα.
                - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public void onDetach()** -> Απελευθέρωση Broadcast Receiver.
        - LightSensorTools
            - **Light_Sensor**
                - **private String check_light(Context context)** -> Υπολογίζει την κατάσταση κινδύνου βάσει τις παρούσας τιμής του αισθητήρα και του αντίστοιχου κατωφλίου.
                - **public  Light_Sensor(final Context context)** -> Θέτει ερώτηση στο σύστημα για τη διαθεσιμότητα του αισθητήρα. Σε περίπτωση θετικής απάντησης προσάπτονται οι κατάλληλοι listeners. Επίσης τοποθετούνται τα κατάλληλα φίλτρα για ενημέρωση αλλαγής κατωφλίων.
            - **LightFragment**
                - **public LightFragment()** -> Αδειος constructor.
                - **public void onCreate(Bundle savedInstanceState)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)** -> Ορίζει τα γραφικά στοιχεία για την παρουσίαση των τιμών που επιστρεφει ο αισθητήρας.
                - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public void onDetach()** -> Απελευθέρωση Broadcast Receiver.
            - **SetLightFragment**
                - **public SetLightFragment()** -> Αδειος constructor.
                - **public void onCreate(Bundle savedInstanceState)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)** -> Ορίζει τα γραφικά στοιχεία για την παρουσίαση και ρύθμιση των κατωφλίων του αισθητήρα.
                - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public void onDetach()** -> Απελευθέρωση Broadcast Receiver.
        - LinearAcceleratorSensorTools
            - **Linear_Accelerator_Sensor**
                - **private String check_linear_accerelator(Double reading, Double threshold, Context context)** -> Υπολογίζει την κατάσταση κινδύνου βάσει τις παρούσας τιμής του αισθητήρα και του αντίστοιχου κατωφλίου.
                - **public Linear_Accelerator_Sensor(final Context context)** -> Θέτει ερώτηση στο σύστημα για τη διαθεσιμότητα του αισθητήρα. Σε περίπτωση θετικής απάντησης προσάπτονται οι κατάλληλοι listeners. Επίσης τοποθετούνται τα κατάλληλα φίλτρα για ενημέρωση αλλαγής κατωφλίων.
            - **LinearAcceleratorFragment**
                - **public LinearAcceleratorFragment()** -> Αδειος constructor.
                - **public void onCreate(Bundle savedInstanceState)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)** -> Ορίζει τα γραφικά στοιχεία για την παρουσίαση των τιμών που επιστρεφει ο αισθητήρας.
                - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public void onDetach()** -> Απελευθέρωση Broadcast Receiver.
            - **SetLinearAcceleratorFragment**
                - **public SetLinearAcceleratorFragment()** -> Αδειος constructor.
                - **public void onCreate(Bundle savedInstanceState)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)** -> Ορίζει τα γραφικά στοιχεία για την παρουσίαση και ρύθμιση των κατωφλίων του αισθητήρα.
                - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public void onDetach()** -> Απελευθέρωση Broadcast Receiver.
        - ProximitySensorTools
            - **Proximity_Sensor**
                - **private String check_proximity(Context context)** -> Υπολογίζει την κατάσταση κινδύνου βάσει τις παρούσας τιμής του αισθητήρα και του αντίστοιχου κατωφλίου.
                - **public  Proximity_Sensor(final Context context)** -> Θέτει ερώτηση στο σύστημα για τη διαθεσιμότητα του αισθητήρα. Σε περίπτωση θετικής απάντησης προσάπτονται οι κατάλληλοι listeners. Επίσης τοποθετούνται τα κατάλληλα φίλτρα για ενημέρωση αλλαγής κατωφλίων.
            - **ProximityFragment**
                - **public ProximityFragment()** -> Αδειος constructor.
                - **public void onCreate(Bundle savedInstanceState)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)** -> Ορίζει τα γραφικά στοιχεία για την παρουσίαση των τιμών που επιστρεφει ο αισθητήρας.
                - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public void onDetach()** -> Απελευθέρωση Broadcast Receiver.
            - **SetProximityFragment**
                - **public SetProximityFragment()** -> Αδειος constructor.
                - **public void onCreate(Bundle savedInstanceState)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)** -> Ορίζει τα γραφικά στοιχεία για την παρουσίαση και ρύθμιση των κατωφλίων του αισθητήρα.
                - **public void onAttach(Context context)** -> Ως ορίζεται η λειτουργεία στην υπερκλάση.
                - **public void onDetach()** -> Απελευθέρωση Broadcast Receiver.