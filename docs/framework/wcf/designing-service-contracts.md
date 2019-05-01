---
title: Projektowanie kontraktów usług
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 68ea866b736350b8a393d1f4788e4b08754e5ab4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785037"
---
# <a name="designing-service-contracts"></a>Projektowanie kontraktów usług
W tym temacie opisano, jakie usługi zamówień są, jak są one definiowane, jakie operacje są dostępne (i wpływ na podstawowej wymianę komunikatów), jakiego typu dane są używane i innych problemów, które ułatwiają Projektuj operacje, które spełniają wymagania wymagania dotyczące scenariusza.  
  
## <a name="creating-a-service-contract"></a>Tworzenie kontraktu usługi  
 Usługi prezentują liczbę operacji. W aplikacji Windows Communication Foundation (WCF), należy zdefiniować operacje, tworząc metody i oznaczenie go atrybutem <xref:System.ServiceModel.OperationContractAttribute> atrybutu. Następnie, aby utworzyć kontrakt usługi, zgrupować operacji albo deklarując oznaczona za pomocą interfejsu <xref:System.ServiceModel.ServiceContractAttribute> atrybutu lub przez definiowanie ich w klasie oznaczonej przy użyciu tego samego atrybutu. (Na przykład podstawowe, zobacz [jak: Definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).)  
  
 Wszystkie metody, które nie mają <xref:System.ServiceModel.OperationContractAttribute> atrybutów nie są operacje usług i nie są udostępniane przez usługi WCF.  
  
 Podczas projektowania kontraktu usługi, w tym temacie opisano następujące decyzje:  
  
- Określa, czy używać klas lub interfejsów.  
  
- Jak określić typy danych, które chcesz wymienić.  
  
- Typy wzorców programu exchange, których można użyć.  
  
- Czy istnieje możliwość wymagania dotyczące zabezpieczeń jawne część Umowy.  
  
- Ograniczenia dotyczące operacji wejścia i wyjścia.  
  
## <a name="classes-or-interfaces"></a>Klas lub interfejsów  
 Klasy i interfejsy reprezentuje zbiór funkcji i w związku z tym, zarówno może służyć do definiowania kontraktu usługi WCF. Zaleca się jednak, aby używać interfejsów, ponieważ modelują one bezpośrednio kontraktów usług. Bez konieczności implementowania interfejsów nie więcej niż definiowanie grup metodami z podpisami niektórych. Implementuj interfejs kontrakt usługi i udało Ci się wdrożyć usługi WCF.  
  
 Wszystkie zalety zarządzane interfejsy dotyczą interfejsy kontraktu usługi:  
  
- Interfejsy kontraktu usługi można rozszerzyć dowolną liczbę inne interfejsy kontraktu usługi.  
  
- Pojedyncza klasa może implementować dowolną liczbę kontraktów usług, zaimplementowanie tych interfejsów kontraktu usługi.  
  
- Implementację kontraktu usługi można zmodyfikować, zmieniając implementacji interfejsu, podczas gdy kontrakt usługi pozostają bez zmian.  
  
- Możesz wersji usługi przez zaimplementowanie interfejsu stary i nowy. Stare klienci łączą się z oryginalnej wersji, podczas gdy nowsze klienci mogą łączyć się nowsza wersja.  
  
> [!NOTE]
>  Gdy dziedziczy z innych interfejsów kontraktu usługi, nie można zastąpić właściwości operacji, np. nazwę lub przestrzeń nazw. Jeśli użytkownik spróbuje to zrobić, należy utworzyć nową operację bieżącej umowy serwisowej.  
  
 Na przykład utworzyć kontrakt usługi przy użyciu interfejsu, zobacz [jak: Tworzenie usługi przy użyciu interfejsu kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Można jednak umożliwia klasę definiowanie kontraktu usługi i zaimplementuj umowy w tym samym czasie. Zaletą tworzenia usług dzięki zastosowaniu <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> bezpośrednio do klasy i metody w klasie odpowiednio jest szybkość i prostota. Wady są, że zarządzanych klas nie obsługują wielokrotnego dziedziczenia, a w rezultacie ich może zawierać implementację tylko jednego kontraktu usługi w danym momencie. Ponadto wszelkie modyfikacje podpisów klasy lub metody modyfikuje publicznego kontraktu dla tej usługi, który może uniemożliwić przy użyciu usługi przez klientów zostały zmodyfikowane. Aby uzyskać więcej informacji, zobacz [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Na przykład, który używa klasy, aby utworzyć kontrakt usługi i implementuje go w tym samym czasie, zobacz [jak: Tworzenie usługi za pomocą klasy kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 W tym momencie należy zrozumieć różnicę między definiowanie kontraktu usługi usługi przy użyciu interfejsu i za pomocą klasy. Następnym krokiem jest podejmowania decyzji, jakie dane mogą być przekazywane i z powrotem między usługą i swoich klientów.  
  
## <a name="parameters-and-return-values"></a>Parametry i zwracane wartości  
 Każda operacja ma wartość zwracaną i parametr, nawet jeśli są one `void`. Jednak w przeciwieństwie do metody lokalnego, w którym można przekazać odwołania do obiektów z jednego obiektu do drugiego, operacje usług nie przekazuj odwołania do obiektów. Zamiast tego Przekaż kopii obiektów.  
  
 Jest to istotne, ponieważ każdy typ używany w parametrze lub zwracana wartość musi być możliwy do serializacji; oznacza to musi istnieć możliwość konwersji obiektu tego typu do strumienia bajtów i ze strumienia bajtów na obiekt.  
  
 Typy pierwotne są możliwe do serializacji, domyślnie, jak wiele typów w .NET Framework.  
  
> [!NOTE]
>  Wartość nazwy parametrów w podpisie operacji są częścią kontraktu i jest uwzględniana wielkość liter. Jeśli chcesz używać tej samej nazwy parametru lokalnie, ale zmianę nazwy opublikowanej metadanych, zobacz <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.  
  
#### <a name="data-contracts"></a>Kontrakty danych  
 Zorientowane na usługę aplikacje, takie jak aplikacje Windows Communication Foundation (WCF) są przeznaczone do współdziałania z usługami najszerszych możliwych liczb aplikacje klienckie w Microsoft i na platformach firmy Microsoft. Najszerszych możliwych współdziałania, zalecane jest oznaczeniu typów z <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów, aby utworzyć kontrakt danych, który jest częścią kontraktu usługi, która opisuje dane, operacje usługi Program Exchange.  
  
 Kontrakty danych są umowami zoptymalizowany pod kątem w stylu: Nie typu lub składowej danych jest serializowana, chyba że wyraźnie zastosujesz atrybut kontraktu danych. Kontrakty danych nie są powiązane z zakresem dostępu kodu zarządzanego: Elementy członkowskie danych prywatnych można serializować i wysłane w innym miejscu, aby być publicznie dostępne. (Aby uzyskać przykład podstawowego kontraktu danych, zobacz [jak: Tworzenie podstawowego kontraktu danych dla klasy lub struktury](../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) Usługi WCF obsługuje definicję podstawowych komunikaty protokołu SOAP, które umożliwiają funkcjonalności operacji, a także serializacji typów danych do i z treści wiadomości. Tak długo, jak Twoje typy danych są możliwe do serializacji, nie trzeba myśleć o podstawowej infrastruktury wymiany komunikatów, przy projektowaniu operacji.  
  
 Mimo że używa Typowa aplikacja usługi WCF <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów do tworzenia kontraktów danych do operacji, można użyć innych mechanizmów serializacji. Standardowa <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.IXmlSerializable> wszystkich mechanizmów współpracują w celu obsługi serializacji typów danych w podstawowej komunikaty protokołu SOAP, wykonujących je z jednej aplikacji na inny. Można używać więcej strategie serializacji, jeśli typów danych wymagają specjalnych pomocy technicznej. Aby uzyskać więcej informacji na temat opcji do serializacji typów danych w aplikacji WCF zobacz [Określanie transferu danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Mapowanie parametrów i zwracanych wartości do wymiany komunikatów  
 Operacje usługi są obsługiwane przez bazowego wymiany wiadomości protokołu SOAP, związane z transferem danych aplikacji i z powrotem, oprócz danych wymaganych przez aplikację do obsługi określonych standardowych zabezpieczeń, transakcji i funkcje związane z sesji. Ponieważ jest to możliwe, decyduje o podpis operacji usługi, w niektórych podstawowych *wymiany komunikatów* (MEP) obsługujące transferu danych i funkcji, operacja wymaga. Można określić trzy wzorce w modelu programowania usługi WCF: żądanie/nietypizowana odpowiedź, jednokierunkowe i wzorców dwukierunkowego wiadomości.  
  
##### <a name="requestreply"></a>Żądanie/nietypizowana odpowiedź  
 Wzorzec żądanie/nietypizowana odpowiedź jest jeden w którym żądanie nadawcy (aplikacja kliencka) otrzyma odpowiedź za pomocą którego są skorelowane żądanie. Jest to domyślna MEP, ponieważ obsługa operacji, w którym jeden lub więcej parametrów są przekazywane do operacji i wartość zwracana jest przekazywany do obiektu wywołującego. Na przykład następująca C# przykładowy kod przedstawia operacji usług w warstwie podstawowa, która przyjmuje jeden ciąg i zwraca wartość typu ciąg.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Poniżej przedstawiono równoważny kod języka Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Ta sygnatura operacji nakazują formularza podstawowego wymianę komunikatów. Brak korelacji istniał, usługi WCF nie może sprawdzić dla operacji, która ma wartość zwracaną.  
  
 Należy zauważyć, że chyba że określisz innego podstawowego wzorca komunikatu, nawet operacje usług, które zwracają `void` (`Nothing` w języku Visual Basic) są żądanie/nietypizowana odpowiedź wymianę komunikatów. Wynik operacji jest, chyba że klient wywołuje operację asynchronicznie, klient zatrzymuje przetwarzanie otrzymanie zwracany komunikat o nawet, jeśli ten komunikat jest pusty w przypadku normalnych. Następujące C# przykładowy kod przedstawia operacją, która nie zwraca do momentu otrzymania przez klienta pusty komunikat odpowiedzi.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Poniżej przedstawiono równoważny kod języka Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 Poprzedni przykład może zmniejszyć wydajność klienta i czas odpowiedzi operacji zajmuje dużo czasu wykonywania, ale istnieją zalety łączenia żądanie/nietypizowana odpowiedź operacji nawet gdy zwracają `void`. Najbardziej oczywistym znajduje się czy błędach SOAP mogą być zwracane w komunikacie odpowiedzi, co oznacza, że jakiegoś warunku błędu związanych z usługą wystąpiło, w komunikacji lub przetwarzania. Błędy protokołu SOAP, które są określone w kontrakcie usługi są przekazywane do aplikacji klienckiej jako <xref:System.ServiceModel.FaultException%601> obiektu, w którym parametr typu jest typu określonego w kontrakcie usługi. To ułatwia zgłaszających klientów o warunkach błędów w usługach WCF. Aby uzyskać więcej informacji dotyczących wyjątków, błędów SOAP oraz obsługi błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Aby zapoznać się przykładem żądanie/nietypizowana odpowiedź usługi i klienta, zobacz [jak: Tworzenie kontraktu "żądanie-odpowiedź"](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Aby uzyskać więcej informacji na temat problemów ze wzorcem "żądanie-odpowiedź" zobacz [usługi "żądanie-odpowiedź"](../../../docs/framework/wcf/feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Jednokierunkowe  
 Jeśli klient aplikacja usługi WCF nie ma oczekiwać na ukończenie tej operacji, nie przetwarza błędach SOAP operacji można określić wzorzec komunikat jednokierunkowy. Operacja jednokierunkowa jest jeden w którym klient wywołuje operację i kontynuuje przetwarzanie po WCF zapisuje komunikat do sieci. Zwykle oznacza to, że chyba, że dane są wysyłane w wiadomości wychodzących jest bardzo duża klient będzie nadal działać niemal natychmiast (chyba że występuje błąd podczas wysyłania danych). Tego rodzaju wymiany komunikatów obsługuje zachowanie podobne zdarzenia z klienta do aplikacji usługi.  
  
 Wymianę komunikatów, w której jeden komunikat jest wysyłany i nie są odbierane nie obsługuje operacji usługi, która określa wartość zwracaną innych niż `void`; w takim przypadku <xref:System.InvalidOperationException> jest zgłaszany wyjątek.  
  
 Żaden komunikat zwracany oznacza również, że może być błąd protokołu SOAP, nie zwrócone do wskazują błędy przetwarzania lub komunikacji. (Podczas komunikowania się informacje o błędzie podczas operacji to operacje jednokierunkowe wymaga wymiany komunikatów dwukierunkowe).  
  
 Aby określić exchange komunikat jednokierunkowy, operacji, która zwraca `void`ustaw <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `true`, jak w następujących C# przykładowy kod.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Poniżej przedstawiono równoważny kod języka Visual Basic.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Ta metoda jest taka sama jak w poprzednim przykładzie żądanie/nietypizowana odpowiedź, ale ustawienie <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwość `true` oznacza, że mimo, że metoda jest identyczny, operacja usługi nie wysyła komunikat zwrotny klienci będą zwracać natychmiast po wychodzące wiadomości ma zostały przekazywane warstwy kanału. Aby uzyskać przykład, zobacz [jak: Tworzenie kontraktu jednokierunkowego](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md). Aby uzyskać więcej informacji na temat jednokierunkowe wzorzec zobacz [usług One-Way](../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Dupleks  
 Dwukierunkowe wzorzec charakteryzuje się możliwości usługi i klienta do wysyłania wiadomości do siebie nawzajem niezależne przeprowadzanych przy użyciu jednokierunkowego lub komunikatów żądań/odpowiedzi. Ten formularz komunikacja dwukierunkowa jest przydatna dla usług, które muszą komunikować się bezpośrednio do klienta lub asynchronicznej obsługi obok wymianę komunikatów, w tym zachowanie podobne zdarzenia.  
  
 Wzorzec dwukierunkowego jest nieco bardziej skomplikowane niż żądanie/nietypizowana odpowiedź lub wzorce jednokierunkowe ze względu na dodatkowe mechanizm komunikacji z klientem.  
  
 Aby zaprojektować kontrakt dupleksowy, musi również projektowanie kontrakt wywołania zwrotnego i przypisać typ ten kontrakt wywołania zwrotnego do <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> właściwość <xref:System.ServiceModel.ServiceContractAttribute> atrybut, który oznacza umowy serwisowej.  
  
 Aby zaimplementować wzorzec dupleksowy, należy utworzyć drugi interfejs, który zawiera deklaracje metody, które są wywoływane na komputerze klienckim.  
  
 Aby uzyskać przykład tworzenia usługi i klienta, który uzyskuje dostęp do tej usługi, zobacz [jak: Tworzenie kontraktu dwukierunkowego](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md) i [jak: Uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Przykładowy pracy [dwukierunkowego](../../../docs/framework/wcf/samples/duplex.md). Aby uzyskać więcej informacji na temat problemów za pomocą kontrakty dwukierunkowe zobacz [usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
> [!CAUTION]
>  Gdy usługa odbiera komunikat dwukierunkowego, wygląda na `ReplyTo` elementu w tej wiadomości przychodzących, aby określić, gdzie wysyłać odpowiedzi. Jeśli nie jest zabezpieczony kanał, który jest używany do odbierania wiadomości, a następnie niezaufanego klienta może wysłać złośliwy komunikat z na komputerze docelowym `ReplyTo`, prowadzącego do typu "odmowa usługi (DOS) tej maszyny docelowej".  
  
##### <a name="out-and-ref-parameters"></a>Poza i parametry Ref  
 W większości przypadków można użyć `in` parametrów (`ByVal` w języku Visual Basic) i `out` i `ref` parametrów (`ByRef` w języku Visual Basic). Ponieważ zarówno `out` i `ref` parametry oznaczają, że dane są zwracane z operacją, sygnaturę operacji, takich jak następujące określa operacji żądanie/nietypizowana odpowiedź jest wymagana, nawet jeśli podpis operacji zwraca `void`.  
  
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
  
 Jedynym wyjątkiem są te przypadki, w których swój podpis ma określonej struktury. Na przykład, można użyć <xref:System.ServiceModel.NetMsmqBinding> powiązania do komunikowania się z klientami tylko wtedy, gdy metody używane do deklarowania operacji zwraca `void`; może istnieć bez wartości danych wyjściowych, czy jest to wartość zwracaną `ref`, lub `out` parametru.  
  
 Ponadto, za pomocą `out` lub `ref` parametrów wymaga, aby wykonać operację miały bazowego komunikat odpowiedzi, żeby ponownie zmodyfikowanego obiektu. Jeśli operacja jest operacji jednokierunkowych <xref:System.InvalidOperationException> wyjątek w czasie wykonywania.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Określ poziom ochrony wiadomości na kontrakt  
 Podczas projektowania Twoja Umowa, trzeba także wybrać poziom ochrony komunikatów, usług, które implementują Twoja Umowa. Jest to konieczne tylko wtedy, gdy zabezpieczenia komunikatów jest stosowany do powiązania w kontraktu punktu końcowego. Jeśli powiązanie ma zabezpieczeń wyłączona (to znaczy, jeśli ustawia powiązania dostarczane przez system <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> wartość <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>), a następnie nie trzeba wybrać poziom ochrony komunikatu dla kontraktu. W większości przypadków powiązania dostarczane przez system za pomocą zastosowano zabezpieczenia na poziomie wiadomości zapewniają wystarczający poziom ochrony i nie należy wziąć pod uwagę poziom ochrony dla każdej operacji lub dla każdego komunikatu.  
  
 Poziom ochrony jest wartość, która określa, czy wiadomości (lub części wiadomości) obsługujące usługi są podpisane, podpisane i szyfrowane lub wysyłane bez podpisy i szyfrowania. Można ustawić poziom ochrony w różnych zakresach: Na poziomie usług dla określonej operacji dla komunikatu w ramach tej operacji lub części komunikatu. Ustawione w jednym zakresie wartości stają się wartością domyślną dla mniejszych zakresach, chyba że jawnie przesłonięte. Jeśli Konfiguracja powiązania nie może zapewnić poziom ochrony minimalne wymagane dla kontraktu, jest zgłaszany wyjątek. I nie wartości poziomu ochrony jawnie ustawione na kontrakt, Konfiguracja powiązania określa poziom ochrony dla wszystkich wiadomości, jeśli powiązanie zabezpieczeń komunikatów. Jest to zachowanie domyślne.  
  
> [!IMPORTANT]
>  Podjęcie decyzji o jawnie ustawić różne zakresy kontraktu na wartość mniejszą niż poziom pełnej ochrony <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> zazwyczaj jest to decyzja, który zamienia pewien stopień zabezpieczeń, aby zwiększyć wydajność. W takich przypadkach decyzje muszą obracać wokół operacji i wartość danych, które są. Aby uzyskać więcej informacji, zobacz [zabezpieczania usług](../../../docs/framework/wcf/securing-services.md).  
  
 Na przykład, poniższy kod nie ustaw <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> lub <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> właściwości kontraktu.  
  
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
  
 Podczas interakcji z `ISampleService` implementacji w punkcie końcowym z domyślną <xref:System.ServiceModel.WSHttpBinding> (wartość domyślna <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, czyli <xref:System.ServiceModel.SecurityMode.Message>), wszystkie komunikaty zostaną zaszyfrowany i podpisany, ponieważ jest to domyślny poziom ochrony. Jednak, gdy `ISampleService` domyślnie jest używana usługa <xref:System.ServiceModel.BasicHttpBinding> (wartość domyślna <xref:System.ServiceModel.SecurityMode>, czyli <xref:System.ServiceModel.SecurityMode.None>), wszystkie komunikaty są wysyłane jako tekst, ponieważ nie istnieje żadne zabezpieczenia dla tego powiązania, a zatem poziom ochrony jest ignorowany (oznacza to, komunikaty nie są szyfrowane ani podpisem). Jeśli <xref:System.ServiceModel.SecurityMode> została zmieniona na <xref:System.ServiceModel.SecurityMode.Message>, a następnie te komunikaty będzie zaszyfrowany i podpisany (ponieważ teraz byłoby wiązania domyślnego poziomu ochrony).  
  
 Jeśli chcesz jawnie określić lub dostosować zgodnie z wymaganiami dla Twojej umowy, ustaw <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> właściwości (lub dowolny z `ProtectionLevel` właściwości na mniejszy zakres) do poziomu wymaga umowy serwisowej. W takim przypadku użycie jawne ustawienie wymaga wiązania Obsługa tego ustawienia co najmniej zakres używany. Na przykład, poniższy przykład kodu Określa jedno <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> wartość jawne, `GetGuid` operacji.  
  
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
  
 To usługa, która to implementuje `IExplicitProtectionLevelSampleService` kontraktu i ma punkt końcowy, który używa domyślnego <xref:System.ServiceModel.WSHttpBinding> (wartość domyślna <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, czyli <xref:System.ServiceModel.SecurityMode.Message>) ma następującą charakterystykę:  
  
- `GetString` Wiadomości operacji czy zaszyfrowana i podpisana.  
  
- `GetInt` Operacji komunikaty są wysyłane jako niezaszyfrowane i bez znaku (to znaczy, gładkie) tekst.  
  
- `GetGuid` Operacji <xref:System.Guid?displayProperty=nameWithType> jest zwracany w komunikacie, który zostaje zaszyfrowany i podpisany.  
  
 Aby uzyskać więcej informacji na temat poziomów ochrony i sposobu ich używania, zobacz [zrozumieć poziom ochrony](../../../docs/framework/wcf/understanding-protection-level.md). Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz [zabezpieczania usług](../../../docs/framework/wcf/securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Wymagania dotyczące innych operacji podpisu  
 Niektóre funkcje aplikacji wymagają szczególnego rodzaju operacji podpisu. Na przykład <xref:System.ServiceModel.NetMsmqBinding> powiązanie obsługuje trwałych usług i klientów, w których aplikację można uruchomić ponownie środku komunikacji i wybierze tam, gdzie ją przerwaliśmy bez brakujące komunikaty. (Aby uzyskać więcej informacji, zobacz [kolejki programu WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).) Jednak operacje trwałe, należy wykonać tylko jedną `in` parametru i nie zwraca wartości.  
  
 Innym przykładem jest użycie <xref:System.IO.Stream> typów w operacjach. Ponieważ <xref:System.IO.Stream> parametr zawiera treść cały komunikat, jeśli dane wejściowe lub wyjściowe (oznacza to, `ref` parametru `out` parametru lub zwracanej wartości) jest typu <xref:System.IO.Stream>to musi być tylko dane wejściowe i dane wyjściowe są określone w sieci Operacja. Ponadto, parametr lub zwracany typ musi być albo <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>, lub <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>. Aby uzyskać więcej informacji na temat strumieni, zobacz [duże ilości danych i przesyłanie strumieniowe](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Nazwy przestrzeni nazw i zaciemniania  
 Nazwy i przestrzenie nazw, typów .NET do definicji kontrakty i operacje są znaczące kontrakty są konwertowane na WSDL i tworzonych i wysyłanych wiadomości kontraktu. W związku z tym, zdecydowanie zaleca się że nazw kontraktu usługi i przestrzenie nazw są jawnie ustawione przy użyciu `Name` i `Namespace` właściwości obsługi wszystkich kontraktu atrybutów, takich jak <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>,  <xref:System.Runtime.Serialization.DataMemberAttribute>i inne atrybuty kontraktu.  
  
 Jeden wynik to jest, jeśli nazwy i przestrzenie nazw nie są jawnie ustawione, użycie zasłanianie IL w zestawie zmienia nazwy typów kontraktu i przestrzenie nazw i powoduje modyfikacji WSDL i wymiany o komunikacji sieciowej, które nie są zwykle. Jeśli nie używaj nazw kontraktu i przestrzenie nazw jawnie, ale zamierza się używać zasłanianie, użyj <xref:System.Reflection.ObfuscationAttribute> i <xref:System.Reflection.ObfuscateAssemblyAttribute> atrybutów, aby zapobiec modyfikacji umowy, wpisz nazwy i przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie kontraktu "żądanie-odpowiedź"](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)
- [Instrukcje: Tworzenie kontraktu jednokierunkowego](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)
- [Instrukcje: Tworzenie kontraktu dwukierunkowego](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Określanie transferu danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
- [Określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Korzystanie z sesji](../../../docs/framework/wcf/using-sessions.md)
- [Operacje synchroniczne i asynchroniczne](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
- [Niezawodne usługi](../../../docs/framework/wcf/reliable-services.md)
- [Usługi i transakcje](../../../docs/framework/wcf/services-and-transactions.md)
