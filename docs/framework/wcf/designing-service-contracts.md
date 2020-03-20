---
title: Projektowanie kontraktów usług
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 37723011d69e8ea2ead3f7a30a30898dede054cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176685"
---
# <a name="designing-service-contracts"></a>Projektowanie kontraktów usług
W tym temacie opisano, jakie są umowy serwisowe, jak są definiowane, jakie operacje są dostępne (i implikacje dla podstawowych wymian komunikatów), jakie typy danych są używane i inne problemy, które pomagają w projektowaniu operacji, które spełniają wymagania dotyczące scenariusza.  
  
## <a name="creating-a-service-contract"></a>Tworzenie umowy serwisowej  
 Usługi ujawniają szereg operacji. W aplikacjach Windows Communication Foundation (WCF) zdefiniuj operacje, tworząc metodę i oznaczając ją atrybutem. <xref:System.ServiceModel.OperationContractAttribute> Następnie, aby utworzyć umowę serwisową, zgrupuj swoje operacje, deklarując <xref:System.ServiceModel.ServiceContractAttribute> je w interfejsie oznaczonym atrybutem lub definiując je w klasie oznaczonej tym samym atrybutem. (W podstawowym przykładzie zobacz [Jak: Definiowanie umowy serwisowej.)](how-to-define-a-wcf-service-contract.md)  
  
 Wszelkie metody, które <xref:System.ServiceModel.OperationContractAttribute> nie mają atrybutu nie są operacje usługi i nie są udostępniane przez usługi WCF.  
  
 W tym temacie opisano następujące punkty decyzyjne podczas projektowania umowy serwisowej:  
  
- Czy używać klas lub interfejsów.  
  
- Jak określić typy danych, które chcesz wymienić.  
  
- Typy wzorców wymiany, których można użyć.  
  
- Czy można dokonać jawne wymagania dotyczące zabezpieczeń część umowy.  
  
- Ograniczenia dotyczące danych wejściowych i wyjściowych operacji.  
  
## <a name="classes-or-interfaces"></a>Klasy lub interfejsy  
 Zarówno klasy, jak i interfejsy reprezentują grupowanie funkcji i w związku z tym oba mogą służyć do definiowania umowy serwisowej WCF. Jednak zaleca się, aby używać interfejsów, ponieważ bezpośrednio modelu umów serwisowych. Bez implementacji interfejsy nie więcej niż zdefiniować grupowanie metod z niektórych podpisów. Zaimplementuj interfejs umowy serwisowej i zaimplementowano usługę WCF.  
  
 Wszystkie zalety interfejsów zarządzanych mają zastosowanie do interfejsów umowy serwisowej:  
  
- Interfejsy umowy serwisowej można rozszerzyć dowolną liczbę innych interfejsów umowy serwisowej.  
  
- Jedna klasa może zaimplementować dowolną liczbę umów serwisowych, implementując te interfejsy umów serwisowych.  
  
- Można zmodyfikować implementację umowy serwisowej, zmieniając implementację interfejsu, podczas gdy umowa serwisowa pozostaje taka sama.  
  
- Można wersji usługi implementując stary interfejs i nowy. Starzy klienci łączą się z oryginalną wersją, podczas gdy nowsi klienci mogą łączyć się z nowszą wersją.  
  
> [!NOTE]
> Dziedzicząc z innych interfejsów umowy serwisowej, nie można zastąpić właściwości operacji, takich jak nazwa lub obszar nazw. Jeśli spróbujesz to zrobić, należy utworzyć nową operację w bieżącym umowie serwisowej.  
  
 Na przykład przy użyciu interfejsu do tworzenia umowy serwisowej, zobacz [Jak: Tworzenie usługi z interfejsem umowy](./feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Można jednak użyć klasy do definiowania umowy serwisowej i implementowania tej umowy w tym samym czasie. Zaletą tworzenia usług przez zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> i bezpośrednio do klasy i metod w klasie, odpowiednio, jest szybkość i prostota. Wadą jest to, że klasy zarządzane nie obsługują wielu dziedziczenia i w rezultacie mogą implementować tylko jedną umowę serwisową w czasie. Ponadto wszelkie modyfikacje podpisów klasy lub metody modyfikuje umowy publicznej dla tej usługi, co może uniemożliwić niezmodyfikowanych klientów z wykorzystaniem usługi. Aby uzyskać więcej informacji, zobacz [Wdrażanie umów serwisowych](implementing-service-contracts.md).  
  
 Na przykład, który używa klasy do utworzenia umowy serwisowej i implementuje ją w tym samym czasie, zobacz [Jak: Tworzenie usługi z klasą kontraktu](./feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 W tym momencie należy zrozumieć różnicę między definiowanie umowy serwisowej przy użyciu interfejsu i przy użyciu klasy. Następnym krokiem jest podjęcie decyzji, jakie dane mogą być przekazywane tam iz powrotem między usługą i jej klientów.  
  
## <a name="parameters-and-return-values"></a>Parametry i wartości zwracane  
 Każda operacja ma wartość zwracaną i parametr, nawet jeśli są `void`to . Jednak w przeciwieństwie do metody lokalnej, w której można przekazać odwołania do obiektów z jednego obiektu do drugiego, operacje usługi nie przekazują odwołań do obiektów. Zamiast tego przekazują kopie obiektów.  
  
 Jest to istotne, ponieważ każdy typ używany w parametrze lub wartości zwracanej musi być serializable; oznacza to, że musi istnieć możliwość konwersji obiektu tego typu do strumienia bajtów i ze strumienia bajtów do obiektu.  
  
 Typy pierwotne są serializable domyślnie, podobnie jak wiele typów w .NET Framework.  
  
> [!NOTE]
> Wartość nazw parametrów w podpisie operacji są częścią umowy i są rozróżniane wielkość liter. Jeśli chcesz użyć tej samej nazwy parametru lokalnie, ale zmodyfikować <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>nazwę w opublikowanych metadanych, zobacz .  
  
#### <a name="data-contracts"></a>Kontrakty danych  
 Aplikacje zorientowane na usługi, takie jak Windows Communication Foundation (WCF), są przeznaczone do współpracy z możliwie najszerszą liczbą aplikacji klienckich na platformach microsoft i innych firm. W celu uzyskania jak najszerszej współdziałania zaleca się <xref:System.Runtime.Serialization.DataContractAttribute> oznaczenie typów atrybutami i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutami w celu utworzenia kontraktu na dane, która jest częścią umowy serwisowej opisującej dane, które są wymieniane przez operacje serwisowe.  
  
 Kontrakty danych są kontrakty opt-in stylu: żaden typ lub element członkowski danych jest szeregowany, chyba że jawnie zastosować atrybut umowy danych. Kontrakty danych nie są związane z zakresem dostępu kodu zarządzanego: Prywatne elementy członkowskie danych mogą być serializowane i wysyłane w innym miejscu, aby uzyskać do nich dostęp publicznie. (Aby uzyskać podstawowy przykład kontraktu na dane, zobacz [Jak: Tworzenie podstawowego kontraktu danych dla klasy lub struktury](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF obsługuje definicji podstawowych komunikatów PROTOKOŁU SOAP, które umożliwiają działanie funkcji, a także serializacji typów danych do i z treści komunikatów. Tak długo, jak typy danych są serializable, nie trzeba myśleć o podstawowej infrastruktury wymiany komunikatów podczas projektowania operacji.  
  
 Mimo że typowa aplikacja WCF używa <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty do tworzenia kontraktów danych dla operacji, można użyć innych mechanizmów serializacji. Standardowe <xref:System.Runtime.Serialization.ISerializable>i <xref:System.SerializableAttribute> <xref:System.Xml.Serialization.IXmlSerializable> mechanizmy działają w celu obsługi serializacji typów danych do podstawowych komunikatów PROTOKOŁU SOAP, które przenoszą je z jednej aplikacji do drugiej. Można zastosować więcej strategii serializacji, jeśli typy danych wymagają specjalnej pomocy technicznej. Aby uzyskać więcej informacji na temat możliwości serializacji typów danych w aplikacjach WCF, zobacz [Określanie transferu danych w umowach serwisowych](./feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Mapowanie parametrów i wartości powrotu do wymiany komunikatów  
 Operacje usługi są obsługiwane przez podstawową wymianę komunikatów PROTOKOŁU SOAP, które przesyłają dane aplikacji tam iz powrotem, oprócz danych wymaganych przez aplikację do obsługi niektórych standardowych funkcji zabezpieczeń, transakcji i sesji. Ponieważ tak jest w przypadku, podpis operacji usługi dyktuje pewne *wzorzec wymiany wiadomości* podstawowej (MEP), który może obsługiwać transfer danych i funkcje, których wymaga operacja. Można określić trzy wzorce w modelu programowania WCF: żądanie/odpowiedź, jednokierunkowe i dupleksowe wzorce komunikatów.  
  
##### <a name="requestreply"></a>Prośba/odpowiedź  
 Wzorzec żądania/odpowiedzi to taki, w którym nadawca żądania (aplikacja kliencka) otrzymuje odpowiedź, z którą żądanie jest skorelowane. Jest to domyślny poseł do PE, ponieważ obsługuje operację, w której jeden lub więcej parametrów jest przekazywanych do operacji, a wartość zwracana jest przekazywana z powrotem do wywołującego. Na przykład w poniższym przykładzie kodu Języka C# pokazano podstawową operację usługi, która przyjmuje jeden ciąg i zwraca ciąg.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Poniżej przedstawiono równoważny kod języka Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Ten podpis operacji dyktuje formę wymiany wiadomości źródłowych. Jeśli nie istnieje korelacja, WCF nie można określić, dla której operacji wartość zwracana jest przeznaczona.  
  
 Należy zauważyć, że jeśli nie określisz innego `void` wzorca wiadomości źródłowych, nawet operacje usługi, które zwracają (w`Nothing` języku Visual Basic) są wymiana wiadomości żądania/odpowiedzi. Wynik dla operacji jest, że chyba że klient wywołuje operację asynchronicznie, klient zatrzymuje przetwarzania, dopóki nie zostanie odebrany komunikat zwrotny, nawet jeśli ta wiadomość jest pusta w normalnym przypadku. Poniższy przykład kodu Języka C# pokazuje operację, która nie zwraca, dopóki klient nie otrzyma pustej wiadomości w odpowiedzi.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Poniżej przedstawiono równoważny kod języka Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 W poprzednim przykładzie można spowolnić wydajność klienta i czas reakcji, jeśli operacja zajmuje dużo czasu, aby `void`wykonać, ale istnieją zalety, aby zażądać/odpowiedzieć operacji, nawet po powrocie . Najbardziej oczywiste jest to, że błędy protokołu SOAP mogą być zwracane w komunikacie odpowiedzi, co wskazuje, że wystąpił jakiś warunek błędu związanego z usługą, czy w komunikacji lub przetwarzania. Błędy protokołu SOAP, które są określone w umowie serwisowej są przekazywane do aplikacji klienckiej jako <xref:System.ServiceModel.FaultException%601> obiekt, gdzie parametr type jest typem określonym w umowie serwisowej. To sprawia, że powiadamianie klientów o warunkach błędów w usługach WCF jest łatwe. Aby uzyskać więcej informacji na temat wyjątków, błędów protokołu SOAP i obsługi [błędów, zobacz Określanie i obsługa błędów w umowach i usługach](specifying-and-handling-faults-in-contracts-and-services.md). Aby wyświetlić przykład usługi żądania/odpowiedzi i klienta, zobacz [Jak: Tworzenie kontraktu z żądaniem i odpowiedzi](./feature-details/how-to-create-a-request-reply-contract.md). Aby uzyskać więcej informacji na temat problemów ze wzorcem żądanie odpowiedź, zobacz [Usługi żądania odpowiedzi](./feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Jednokierunkowe  
 Jeśli klient aplikacji usługi WCF nie należy czekać na zakończenie operacji i nie przetwarza błędów PROTOKOŁU SOAP, operacja może określić wzorzec komunikatów jednokierunkowych. Operacja jednokierunkowa to operacja, w której klient wywołuje operację i kontynuuje przetwarzanie po zapisaniu WCF zapisu wiadomości do sieci. Zazwyczaj oznacza to, że jeśli dane wysyłane w wiadomości wychodzącej jest bardzo duży, klient kontynuuje uruchamianie niemal natychmiast (chyba że występuje błąd wysyłania danych). Ten typ wzorca wymiany komunikatów obsługuje zachowanie podobne do zdarzenia od klienta do aplikacji usługi.  
  
 Wymiana komunikatów, w której jest wysyłana jedna wiadomość i żadna nie `void`jest odbierana, nie może obsługiwać operacji usługi określającej wartość zwracaną inną niż; w tym <xref:System.InvalidOperationException> przypadku wyjątek.  
  
 Brak komunikatu zwrotnego oznacza również, że nie może być błąd PROTOKOŁU SOAP zwrócone, aby wskazać żadnych błędów w przetwarzaniu lub komunikacji. (Przekazywanie informacji o błędzie, gdy operacje są operacjami jednokierunkowymi, wymaga wzorca wymiany komunikatów dupleksu).  
  
 Aby określić jednokierunkową wymianę komunikatów `void`dla <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> operacji, `true`która zwraca, ustaw właściwość na , jak w poniższym przykładzie kodu C#.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Poniżej przedstawiono równoważny kod języka Visual Basic.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Ta metoda jest identyczna z poprzednim przykładem <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> żądania/odpowiedzi, ale ustawienie właściwości oznacza, `true` że chociaż metoda jest identyczna, operacja usługi nie wysyła komunikatu zwrotnego i klienci zwracają natychmiast po przekazaniu wiadomości wychodzącej do warstwy kanału. Na przykład zobacz [Jak: Tworzenie kontraktu jednokierunkowego](./feature-details/how-to-create-a-one-way-contract.md). Aby uzyskać więcej informacji na temat wzorca jednokierunkowego, zobacz [Usługi jednokierunkowe](./feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Dupleks  
 Wzorzec dupleksu charakteryzuje się możliwością zarówno usługi, jak i klienta do wysyłania wiadomości do siebie niezależnie, czy przy użyciu wiadomości jednokierunkowe lub żądania/odpowiedzi. Ta forma komunikacji dwukierunkowej jest przydatna w przypadku usług, które muszą komunikować się bezpośrednio z klientem lub zapewniając asynchroniczne środowisko po obu stronach wymiany komunikatów, w tym zachowanie podobne do zdarzenia.  
  
 Wzorzec dupleksu jest nieco bardziej złożony niż żądanie/odpowiedź lub wzorce jednokierunkowe ze względu na dodatkowy mechanizm komunikacji z klientem.  
  
 Aby zaprojektować kontrakt dupleksowy, należy również zaprojektować umowę wywołania <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> zwrotnego <xref:System.ServiceModel.ServiceContractAttribute> i przypisać typ tej umowy wywołania zwrotnego do właściwości atrybutu, który oznacza umowę serwisową.  
  
 Aby zaimplementować wzorzec dupleksu, należy utworzyć drugi interfejs, który zawiera deklaracje metody, które są wywoływane na kliencie.  
  
 Na przykład tworzenia usługi i klienta, który uzyskuje dostęp do tej usługi, zobacz [Jak: Tworzenie kontraktu dupleksowego](./feature-details/how-to-create-a-duplex-contract.md) i [jak: Dostęp do usług z umową dupleksu](./feature-details/how-to-access-services-with-a-duplex-contract.md). Aby zapoznać się z próbką roboczą, zobacz [Dupleks](./samples/duplex.md). Aby uzyskać więcej informacji na temat problemów związanych z umowami dupleksowymi, zobacz [Usługi dupleksu](./feature-details/duplex-services.md).  
  
> [!CAUTION]
> Gdy usługa odbiera komunikat dupleksu, `ReplyTo` patrzy na element w tej wiadomości przychodzącej, aby określić, gdzie wysłać odpowiedź. Jeśli kanał, który jest używany do odbierania wiadomości nie jest zabezpieczony, niezaufany `ReplyTo`klient może wysłać złośliwą wiadomość z komputera docelowego, co prowadzi do odmowy usługi (DOS) tego komputera docelowego.  
  
##### <a name="out-and-ref-parameters"></a>Parametry wyjścia i ref  
 W większości przypadków można `in` użyć`ByVal` parametrów (w `ref` języku`ByRef` Visual Basic) i `out` parametrów (w języku Visual Basic). Ponieważ `out` zarówno `ref` parametry, jak i parametry wskazują, że dane są zwracane z operacji, podpis operacji, taki `void`jak poniższy, określa, że operacja żądania/odpowiedzi jest wymagana, nawet jeśli zwraca podpis operacji .  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 Poniżej przedstawiono równoważny kod języka Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 Jedynymi wyjątkami są przypadki, w których podpis ma określoną strukturę. Na przykład można użyć <xref:System.ServiceModel.NetMsmqBinding> powiązania do komunikowania się z klientami `void`tylko wtedy, gdy metoda używana do deklarowania operacji zwraca; nie może być wartość wyjściowa, czy `ref`jest `out` to wartość zwracana, lub parametr.  
  
 Ponadto przy `out` użyciu `ref` lub parametry wymaga, że operacja ma podstawowy komunikat odpowiedzi do przenoszenia zmodyfikowanego obiektu. Jeśli operacja jest operacją jednokierunkową, <xref:System.InvalidOperationException> wyjątek jest zgłaszany w czasie wykonywania.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Określ poziom ochrony wiadomości w umowie  
 Podczas projektowania umowy, należy również zdecydować poziom ochrony wiadomości usług, które implementują umowy. Jest to konieczne tylko wtedy, gdy zabezpieczenia wiadomości są stosowane do powiązania w punkcie końcowym umowy. Jeśli powiązanie ma zabezpieczenia wyłączone (oznacza to, że <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> jeśli powiązanie dostarczone przez system ustawia wartość), <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>nie trzeba decydować o poziomie ochrony wiadomości dla umowy. W większości przypadków powiązania dostarczane przez system z zastosowanymi zabezpieczeniami na poziomie wiadomości zapewniają wystarczający poziom ochrony i nie trzeba brać pod uwagę poziomu ochrony dla każdej operacji lub dla każdej wiadomości.  
  
 Poziom ochrony jest wartością określającą, czy wiadomości (lub części wiadomości), które obsługują usługę, są podpisane, podpisane i zaszyfrowane lub wysyłane bez podpisów lub szyfrowania. Poziom ochrony można ustawić w różnych zakresach: na poziomie usługi, dla określonej operacji, dla wiadomości w ramach tej operacji lub części wiadomości. Wartości ustawione w jednym zakresie stają się wartością domyślną dla mniejszych zakresów, chyba że jawnie zastąpione. Jeśli konfiguracja powiązania nie może zapewnić wymagany minimalny poziom ochrony dla umowy, wyjątek. A gdy żadne wartości poziomu ochrony nie są jawnie ustawione na umowie, konfiguracja powiązania kontroluje poziom ochrony dla wszystkich wiadomości, jeśli powiązanie ma zabezpieczenia wiadomości. Jest to zachowanie domyślne.  
  
> [!IMPORTANT]
> Podjęcie decyzji, czy wyraźnie ustawić różne zakresy umowy na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> mniej niż pełny poziom ochrony jest zazwyczaj decyzją, która handluje pewnym stopniem bezpieczeństwa w celu zwiększenia wydajności. W takich przypadkach decyzje muszą obracać się wokół operacji i wartości danych, które wymieniają. Aby uzyskać więcej informacji, zobacz [zabezpieczanie usług](securing-services.md).  
  
 Na przykład poniższy przykład kodu nie <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> ustawia <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> ani właściwości na umowie.  
  
```csharp  
[ServiceContract]  
public interface ISampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute]  
  public int GetInt();
}  
```  
  
 Poniżej przedstawiono równoważny kod języka Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 Podczas interakcji z `ISampleService` implementacją w punkcie <xref:System.ServiceModel.WSHttpBinding> końcowym z <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>wartością <xref:System.ServiceModel.SecurityMode.Message>domyślną (domyślną , czyli), wszystkie wiadomości są szyfrowane i podpisywane, ponieważ jest to domyślny poziom ochrony. Jednak gdy `ISampleService` usługa jest używana <xref:System.ServiceModel.BasicHttpBinding> z wartością domyślną (domyślna <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.SecurityMode.None>czyli), wszystkie wiadomości są wysyłane jako tekst, ponieważ nie ma zabezpieczeń dla tego powiązania, a więc poziom ochrony jest ignorowany (oznacza to, że wiadomości nie są ani szyfrowane, ani podpisane). Jeśli <xref:System.ServiceModel.SecurityMode> został zmieniony <xref:System.ServiceModel.SecurityMode.Message>na , a następnie te wiadomości będą szyfrowane i podpisane (ponieważ byłoby to teraz domyślny poziom ochrony powiązania).  
  
 Jeśli chcesz jawnie określić lub dostosować wymagania dotyczące ochrony <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> dla umowy, `ProtectionLevel` ustaw właściwość (lub dowolną z właściwości w mniejszym zakresie) do poziomu wymaganego przez umowę serwisową. W takim przypadku przy użyciu jawne ustawienie wymaga powiązania do obsługi tego ustawienia co najmniej dla zakresu używane. Na przykład poniższy przykład kodu <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> określa jedną wartość `GetGuid` jawnie dla operacji.  
  
```csharp  
[ServiceContract]  
public interface IExplicitProtectionLevelSampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.None)]  
  public int GetInt();
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
  public int GetGuid();
}  
```  
  
 Poniżej przedstawiono równoważny kod języka Visual Basic.  
  
```vb  
<ServiceContract()> _
Public Interface IExplicitProtectionLevelSampleService
    <OperationContract()> _
    Public Function GetString() As String
    End Function
  
    <OperationContract(ProtectionLevel := ProtectionLevel.None)> _
    Public Function GetInt() As Integer
    End Function
  
    <OperationContractAttribute(ProtectionLevel := ProtectionLevel.EncryptAndSign)> _
    Public Function GetGuid() As Integer
    End Function
  
End Interface  
```  
  
 Usługa, która implementuje `IExplicitProtectionLevelSampleService` tę umowę i ma punkt <xref:System.ServiceModel.WSHttpBinding> końcowy, <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>który <xref:System.ServiceModel.SecurityMode.Message>używa wartości domyślnej (domyślna , czyli) ma następujące zachowanie:  
  
- Komunikaty `GetString` operacyjne są szyfrowane i podpisane.  
  
- Komunikaty `GetInt` operacji są wysyłane jako niezaszyfrowany i niepodpisany (czyli zwykły) tekst.  
  
- Operacja `GetGuid` <xref:System.Guid?displayProperty=nameWithType> jest zwracana w wiadomości, która jest szyfrowana i podpisana.  
  
 Aby uzyskać więcej informacji na temat poziomów ochrony i sposobu ich używania, zobacz [Opis poziomu ochrony](understanding-protection-level.md). Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz [Zabezpieczanie usług](securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Inne wymagania dotyczące podpisu operacji  
 Niektóre funkcje aplikacji wymagają określonego rodzaju podpisu operacji. Na przykład <xref:System.ServiceModel.NetMsmqBinding> powiązanie obsługuje trwałe usługi i klientów, w którym aplikacja można ponownie uruchomić w środku komunikacji i odebrać, gdzie zostało przerwane bez utraty żadnych komunikatów. (Aby uzyskać więcej informacji, zobacz [Kolejki w WCF](./feature-details/queues-in-wcf.md).) Jednak operacje trwałe musi `in` mieć tylko jeden parametr i nie mają wartości zwracanej.  
  
 Innym przykładem jest <xref:System.IO.Stream> użycie typów w operacjach. Ponieważ <xref:System.IO.Stream> parametr zawiera całą treść wiadomości, jeśli dane wejściowe `ref` lub `out` wyjściowe (czyli parametr, <xref:System.IO.Stream>parametr lub wartość zwracana) jest typu, musi to być jedyne wejście lub wyjście określone w operacji. Ponadto parametr lub typ zwracany musi <xref:System.IO.Stream> <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>być <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>albo , lub . Aby uzyskać więcej informacji o strumieniach, zobacz [Duże dane i przesyłanie strumieniowe](./feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Nazwy, przestrzenie nazw i zaciemnienie  
 Nazwy i przestrzenie nazw typów .NET w definicji kontraktów i operacji są istotne, gdy kontrakty są konwertowane na WSDL i gdy wiadomości umowy są tworzone i wysyłane. W związku z tym zdecydowanie zaleca się, że nazwy umów `Name` serwisowych i przestrzenie nazw są jawnie ustawiane przy `Namespace` użyciu i właściwości wszystkich atrybutów umowy <xref:System.ServiceModel.ServiceContractAttribute>obsługi, takich jak , <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute>, i inne atrybuty umowy.  
  
 Jednym z wyników jest to, że jeśli nazwy i przestrzenie nazw nie są jawnie ustawione, użycie zaciemnienia IL w zestawie zmienia nazwy typów kontraktu i przestrzeni nazw i powoduje zmodyfikowane WSDL i wymiany przewodów, które zazwyczaj nie powiodą się. Jeśli nazwy kontraktów i przestrzeni nazw nie są jawnie ustawiane, ale <xref:System.Reflection.ObfuscationAttribute> zamierzasz użyć zaciemniania, użyj atrybutów i <xref:System.Reflection.ObfuscateAssemblyAttribute> atrybutów, aby zapobiec modyfikacji nazw typów kontraktów i obszarów nazw.  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie kontraktu „żądanie-odpowiedź”](./feature-details/how-to-create-a-request-reply-contract.md)
- [Instrukcje: tworzenie kontraktu jednokierunkowego](./feature-details/how-to-create-a-one-way-contract.md)
- [Instrukcje: tworzenie kontraktu dwukierunkowego](./feature-details/how-to-create-a-duplex-contract.md)
- [Określanie transferu danych w kontraktach usług](./feature-details/specifying-data-transfer-in-service-contracts.md)
- [Określanie i obsługa błędów w kontraktach i usługach](specifying-and-handling-faults-in-contracts-and-services.md)
- [Korzystanie z sesji](using-sessions.md)
- [Operacje synchroniczne i asynchroniczne](synchronous-and-asynchronous-operations.md)
- [Reliable Services](reliable-services.md)
- [Usługi i transakcje](services-and-transactions.md)
