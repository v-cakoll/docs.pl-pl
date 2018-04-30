---
title: Projektowanie kontraktów usług
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
caps.latest.revision: 34
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 14973d3612eb5739e0dfcd7b50409904ab5d6844
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="designing-service-contracts"></a>Projektowanie kontraktów usług
W tym temacie opisano, jakie usługi kontraktów są, jak są zdefiniowane, jakie operacje są dostępne (i wpływem na podstawowym wymiany komunikatów), jakie typy danych są używane i inne problemy, które ułatwiają projektowanie operacje, które spełniają wymagania danego scenariusza.  
  
## <a name="creating-a-service-contract"></a>Tworzenie kontraktu usługi  
 Usługi Udostępnianie liczba operacji. W [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacje, zdefiniuj operacje tworzenia metody i oznaczenie go atrybutem <xref:System.ServiceModel.OperationContractAttribute> atrybutu. Następnie, aby utworzyć kontrakt usługi, grupują działania, poprzez ich zgłaszania interfejsu oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute> atrybut lub poprzez definiowanie je w klasie oznaczonej przez tego samego atrybutu. (Na przykład podstawowa, zobacz [porady: definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).)  
  
 Wszystkie metody, które nie mają <xref:System.ServiceModel.OperationContractAttribute> atrybutów nie są operacji usługi i nie są dostępne w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług.  
  
 W tym temacie opisano następujące punkty decyzyjne podczas projektowania kontraktu usługi:  
  
-   Określa, czy używać interfejsów lub klas.  
  
-   Jak określać typy danych, które chcesz programu exchange.  
  
-   Typy z programu exchange, które można użyć.  
  
-   Określa, czy istnieje możliwość wymagania zabezpieczeń jawne częścią umowy.  
  
-   Ograniczenia dotyczące operacji wejścia i wyjścia.  
  
## <a name="classes-or-interfaces"></a>Interfejsów lub klas  
 Zarówno klasy i interfejsy reprezentują grupowania funkcjonalności i, w związku z tym są używane do definiowania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kontraktu usługi. Zaleca się jednak używać interfejsów, ponieważ ich bezpośrednio modelu kontraktów usług. Bez implementacji interfejsów nie więcej niż definiowanie grup metod z określonych podpisów. Implementowanie interfejsu kontraktu usługi i wdrożeniu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi.  
  
 Wszystkie zalety zarządzane interfejsy dotyczą interfejsy kontraktu usługi:  
  
-   Interfejsy kontraktu usługi można rozszerzyć dowolną liczbę inne interfejsy kontraktu usługi.  
  
-   Klasę można zaimplementować dowolną liczbę kontraktów usług zaimplementowanie te interfejsy kontraktu usługi.  
  
-   Implementacji kontraktu usługi można modyfikować, zmieniając implementacji interfejsu, podczas gdy kontrakt usługi jest taka sama.  
  
-   Możesz wersji usługi zaimplementowanie interfejsu starym i nowym. Stary klienci łączą się z oryginalną wersją podczas nowszych wersji klientów można połączyć do nowszej wersji.  
  
> [!NOTE]
>  Podczas dziedziczenia z innych interfejsów kontraktu usługi, nie można zastąpić właściwości operacji, np. nazwę lub przestrzeń nazw. Jeśli użytkownik spróbuje to zrobić, tworzenia nowej operacji w bieżącym kontraktu usługi.  
  
 Przykład użycia interfejsu, aby utworzyć kontrakt usługi, zobacz [porady: Tworzenie usługi przy użyciu interfejsu kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Można jednak używać klasy definiowanie kontraktu usługi i implementacji tego kontraktu w tym samym czasie. Zaletą tworzenia usług, stosując <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> bezpośrednio do klasy i metody w klasie, odpowiednio jest szybkość i prostota. Wady są zarządzanych klas nie obsługują dziedziczenie wielokrotne, czy w związku z tym ich można tylko zaimplementować jeden kontrakt usługi naraz. Ponadto wszelkie modyfikacje podpisów klasa lub metoda modyfikuje publicznego kontraktu dla tej usługi, co może uniemożliwić klientom zostały zmodyfikowane za pomocą usługi. Aby uzyskać więcej informacji, zobacz [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Na przykład, używa klasy w celu utworzenia kontraktu usługi, który implementuje go w tym samym czasie, zobacz [porady: Tworzenie usługi za pomocą klasy kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 W tym momencie należy zrozumieć różnicę między Definiowanie umowy serwisowej, przy użyciu interfejsu i przy użyciu klasy. Następnym krokiem decyduje, jakie dane mogą zostać przekazane i z powrotem między usługą i klientów.  
  
## <a name="parameters-and-return-values"></a>Parametry i wartości zwracane  
 Każda operacja wymaga wartości zwracanej i parametrów, nawet jeśli są one `void`. Jednak w przeciwieństwie do metodę lokalną, w którym można przekazać odwołania do obiektów z jednego obiektu do innego, operacje usług nie są przekazywane odwołania do obiektów. Zamiast tego przechodzą kopii obiektów.  
  
 Jest to istotne, ponieważ każdy typ użyte w parametrze lub zwracać wartość musi być możliwy do serializacji; oznacza to musi być możliwe do przekonwertowania obiektu tego typu w strumieniu bajtów i ze strumienia bajtów do obiektu.  
  
 Typy pierwotne są domyślnie serializacji, ponieważ wiele typów w programie .NET Framework.  
  
> [!NOTE]
>  Wartość nazwy parametrów w podpisie operacji są częścią kontraktu i jest uwzględniana wielkość liter. Jeśli chcesz używać tej samej nazwy parametru lokalnie, ale zmodyfikować nazwę w opublikowanej metadanych, zobacz <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.  
  
#### <a name="data-contracts"></a>Kontrakty danych  
 Aplikacje zorientowane na usługę, takie jak [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacje są zaprojektowane na potrzeby współdziałania z najszerszych liczba aplikacji klienckich zarówno firmy Microsoft, jak i platform firmy Microsoft. Dla najszerszych możliwych współdziałanie, zalecane jest, aby oznaczyć z typów z <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów, aby utworzyć kontrakt danych, który jest częścią kontraktu usługi, która opisuje dane które operacje usługi Program Exchange.  
  
 Kontrakty danych są umowami uczestnictwa w stylu: nie typu lub członka danych jest serializowany, chyba że jawnie zastosuj atrybut kontraktu danych. Kontrakty danych nie są powiązane z zakresem dostępu kodu zarządzanego: dane prywatne elementy Członkowskie mogą być serializowane i wysyłane jako dostępne publicznie w innych miejscach. (Na przykład podstawowego kontraktu danych, zobacz [porady: Tworzenie podstawowego kontraktu danych dla klasy lub struktury](../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obsługuje definicji podstawowej wiadomości SOAP, które włączyć funkcję wykonać operację, a także serializacji typów danych do i z treści wiadomości. Tak długo, jak typów danych jest możliwy do serializacji, nie trzeba myśleć o podstawowej infrastruktury wymiany komunikatów podczas projektowania operacje.  
  
 Mimo że typowe [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacja używa <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty do utworzenia kontraktów danych dla operacji, można użyć innych mechanizmów serializacji. Standardowe <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.IXmlSerializable> wszystkich mechanizmów pracy do obsługi serializacji typów danych w podstawowej wiadomości SOAP, zawierających je z jedną aplikację do innego. Można wdrożyć więcej strategii serializacji, jeśli typów danych wymagają specjalnych pomocy technicznej. Aby uzyskać więcej informacji o opcjach do serializacji typów danych w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji, zobacz [Określanie transferu danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Mapowanie parametrów i zwracanych wartości do wymiany komunikatów  
 Operacje usług są obsługiwane przez podstawowej wymiany wiadomości SOAP, związane z transferem danych aplikacji i z powrotem, oprócz danych wymaganych przez aplikację do obsługi określonych standardowych zabezpieczeń transakcji i funkcje związane z sesji. Ponieważ jest to możliwe, sygnatura operacji usługi nakazują niektórych podstawowych *wymiany komunikatów* (MEP) obsługujące transferu danych i funkcji, operacja wymaga. Można określić trzy wzorce w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] model programowania: żądanie/odpowiedź, jednokierunkowe i wzorce dupleksu wiadomości.  
  
##### <a name="requestreply"></a>Żądanie i odpowiedź  
 Wzorzec żądanie i odpowiedź jest jednym w którym żądanie nadawcy (aplikacja kliencka) odebrał odpowiedź z którym są korelowane z żądania. Jest to domyślna MEP, ponieważ obsługuje on operacji, w której jeden lub więcej parametrów są przekazywane do działania i wartości zwracanej jest przekazywane z powrotem do wywołującego. Na przykład w poniższym przykładzie kodu C# zawiera operację podstawowej usługi, która przyjmuje jeden ciąg i zwraca wartość typu ciąg.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Poniżej znajduje się równoważne kodu języka Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Ta sygnatura operacji nakazują formularza podstawowego wymiany wiadomości. Jeśli korelacji nie istniał, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] nie można określić dla operacji, które ma wartość zwracaną.  
  
 Należy pamiętać, że jeśli nie podasz inną podstawowej komunikatów, nawet operacji usługi, które zwracają `void` (`Nothing` w języku Visual Basic) są wymiany komunikatów żądania/odpowiedzi. Wynik dla operacji jest czy chyba, że klient wywołuje operację asynchronicznie, klient zatrzymuje przetwarzanie do momentu otrzymania komunikat zwrotny, mimo że ten komunikat jest pusty w przypadku normalnych. Poniższy przykład kodu C# zawiera operację, która nie zwraca do momentu otrzymania przez klienta jest pusty komunikat odpowiedzi.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Poniżej znajduje się równoważne kodu języka Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 Poprzedni przykład może zmniejszyć wydajność klienta i elastyczność, jeśli operacja trwa zbyt długo do wykonania, ale istnieją pewne zalety operacji żądania/odpowiedzi nawet gdy zwracają `void`. Najbardziej oczywisty znajduje się czy błędach SOAP może być zwracany w odpowiedzi komunikat informujący o tym, że niektóre związane z usługą błąd wystąpił, w komunikacji lub przetwarzania. Błędach SOAP, które są określone w kontrakcie usługi są przekazywane do aplikacji klienckiej jako <xref:System.ServiceModel.FaultException%601> obiektu, gdy parametr typu jest typ określony w kontrakcie usługi. Dzięki temu klienci powiadamiające o warunkach błędów w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług łatwe. Aby uzyskać więcej informacji na temat wyjątków, błędach SOAP i obsługa błędów zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Aby zapoznać się przykładem żądania/odpowiedzi usługi i klienta, zobacz [porady: tworzenie kontraktu "żądanie-odpowiedź"](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Aby uzyskać więcej informacji na temat problemów ze wzorcem "żądanie-odpowiedź", zobacz [usługi "żądanie-odpowiedź"](../../../docs/framework/wcf/feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Jednokierunkowe  
 Jeśli klient [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji usługi nie ma oczekiwać na zakończenie operacji i nie może przetwarzać błędach SOAP, operacji można określić jednokierunkowe komunikatów. Operacja jednokierunkowa jest jeden, w którym klient wywołuje operację i kontynuuje przetwarzania po [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zapisuje komunikat w sieci. Zwykle oznacza to, że chyba, że dane są wysyłane w wiadomości wychodzącej jest bardzo dużą klienta wciąż trwa niemal natychmiast (chyba że występuje błąd podczas wysyłania danych). Ten typ wymiany komunikatów obsługuje zachowanie podobne zdarzenia z klienta do aplikacji usługi.  
  
 Wymiany wiadomości, w której jeden komunikat jest wysyłany i nie są odbierane nie obsługuje operacji usługi, który innych niż określa wartość zwracaną `void`; w takim przypadku <xref:System.InvalidOperationException> wyjątku.  
  
 Żaden komunikat zwrotny również oznacza, że może być nie błędu protokołu SOAP zwracanych do wskazuje wszelkie błędy przetwarzania lub komunikacji. (Komunikacji informacji o błędach, gdy operacje są operacji jednokierunkowych wymaga dwukierunkowego wymiany komunikatów).  
  
 Aby określić komunikat jednokierunkowy exchange dla danej operacji, która zwraca `void`ustaw <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `true`, jak w poniższym przykładzie kodu C#.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Poniżej znajduje się równoważne kodu języka Visual Basic.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Ta metoda jest taki sam jak poprzedni przykład żądania/odpowiedzi, ale ustawienie <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `true` oznacza, że metoda ma taki sam, ale operacja usługi nie wysyła komunikat zwrotny, a klienci będą zwracać bezpośrednio po komunikat wychodzący ma zostały przekazane do warstwy kanału. Na przykład zobacz [porady: tworzenie kontraktu One-Way](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md). Aby uzyskać więcej informacji o wzorcu jednokierunkowe, zobacz [usług One-Way](../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Dupleks  
 Wzorzec dupleksu charakteryzuje się możliwość wysyłania wiadomości ze sobą niezależnie czy przy użyciu jednokierunkowego usługę i klienta lub żądania/odpowiedzi, wiadomości. Ten formularz dwukierunkowej komunikacji jest przydatne dla usług, które muszą komunikować się bezpośrednio do klienta lub udostępnia asynchroniczne środowiska do jednej części wiadomości programu exchange, w tym zdarzenia podobne zachowania.  
  
 Wzorzec dupleksu jest nieco bardziej skomplikowane niż żądania/odpowiedzi lub wzorce jednokierunkowe z powodu dodatkowy mechanizm komunikacji z klientem.  
  
 Projektowanie kontrakt dupleksowy, należy także zaprojektować kontrakt wywołania zwrotnego i przypisać typ tego kontraktu wywołania zwrotnego do <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> właściwość <xref:System.ServiceModel.ServiceContractAttribute> atrybut umożliwiający oznaczenie umowy serwisowej.  
  
 Aby zaimplementować wzorzec dupleksowy, należy utworzyć drugi interfejs, który zawiera deklaracje metody, które są wywoływane na kliencie.  
  
 Na przykład tworzenia usługi i klienta, który uzyskuje dostęp do tej usługi, zobacz [porady: tworzenie kontraktu dwukierunkowego](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md) i [porady: usługi dostęp z kontraktu dwukierunkowego](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Dla przykładu pracy, zobacz [dupleksu](../../../docs/framework/wcf/samples/duplex.md). Aby uzyskać więcej informacji na temat problemów przy użyciu kontrakty dwukierunkowe, zobacz [usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
> [!CAUTION]
>  Gdy usługa odbiera komunikat dupleksowy, wygląda na `ReplyTo` element w tej wiadomości przychodzących, aby określić, który ma zostać wysłana odpowiedź. Jeśli nie jest zabezpieczony kanał, który jest używany do odbierania wiadomości, a następnie niezaufanego klienta może wysłać komunikat złośliwego przy komputerze docelowym `ReplyTo`, prowadzących do odmowy usługi (DOS) tego komputera docelowego.  
  
##### <a name="out-and-ref-parameters"></a>Parametry Ref i out  
 W większości przypadków można użyć `in` parametrów (`ByVal` w języku Visual Basic) i `out` i `ref` parametrów (`ByRef` w języku Visual Basic). Ponieważ oba `out` i `ref` parametry wskazują, że dane są zwracane z operacji programu podpisu operacji, takich jak określa, czy operacja żądania/odpowiedzi jest wymagane, nawet jeśli podpis operacji zwraca `void`.  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 Poniżej znajduje się równoważne kodu języka Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 Jedynym wyjątkiem są tych przypadków, w których podpis ma określonej struktury. Na przykład można użyć <xref:System.ServiceModel.NetMsmqBinding> powiązanie do komunikacji z klientami tylko wtedy, gdy metodę używaną do deklarowania operacji zwraca `void`; może istnieć bez wartości danych wyjściowych, czy jest wartość zwracaną `ref`, lub `out` parametru.  
  
 Ponadto przy użyciu `out` lub `ref` parametrów musi mieć operacji podstawowej komunikat odpowiedzi do przenoszenia wstecz zmodyfikowanego obiektu. W przypadku operacji jednokierunkowych operacji <xref:System.InvalidOperationException> wyjątek w czasie wykonywania.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Określ poziom ochrony wiadomości kontraktu  
 Podczas projektowania umowy, należy również postanowić, poziom ochrony wiadomości usług, które implementują umowy. Jest to konieczne tylko wtedy, gdy zabezpieczenia wiadomości jest stosowany do powiązania w kontraktu punktu końcowego. Jeśli powiązanie jest wyłączone zabezpieczeń (to znaczy, jeśli powiązania dostarczane przez system ustawia <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> wartość <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>), a następnie jest konieczne podejmowanie decyzji o poziom ochrony wiadomości dla kontraktu. W większości przypadków powiązania dostarczane przez system z zabezpieczeniami na poziomie komunikatu stosowane zapewniają wystarczający poziom ochrony i nie należy wziąć pod uwagę poziom ochrony dla każdej operacji lub dla każdego komunikatu.  
  
 Poziom ochrony jest wartość, która określa, czy wiadomości (lub części wiadomości) obsługujące usługi są podpisywane, podpisane i szyfrowane lub wysyłane bez podpisy i szyfrowania. Można ustawić poziom ochrony w różnych zakresów: na poziomie usługi dla określonej operacji, wiadomości w tej operacji lub części komunikatu. Wartości ustawione w jednym zakresie staje się wartością domyślną dla mniejszych zakresach, chyba że jawnie przesłonięte. Jeśli Konfiguracja powiązania nie zapewnia poziom ochrony minimalne wymagane dla kontraktu, jest zwracany wyjątek. I kontraktu jawnie ustawione wartości poziomu ochrony, Konfiguracja powiązania określa poziom ochrony dla wszystkich wiadomości, jeśli wiązanie zabezpieczeń komunikatów. Jest to zachowanie domyślne.  
  
> [!IMPORTANT]
>  Podjęcie decyzji o jawnie ustaw różne zakresy kontraktu na wartość mniejszą niż poziom pełnej ochrony <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> jest zazwyczaj decyzji, które zajmują pewnym stopniu zabezpieczeń w celu zwiększenia wydajności. W takich przypadkach swoje decyzje dotyczące muszą obracać wokół działania i wartości danych, które wymieniają. Aby uzyskać więcej informacji, zobacz [zabezpieczania usług](../../../docs/framework/wcf/securing-services.md).  
  
 Na przykład w poniższym przykładzie kodu nie ustawia albo <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> lub <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> właściwości kontraktu.  
  
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
  
 Poniżej znajduje się równoważne kodu języka Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 Podczas interakcji z `ISampleService` implementacja punktu końcowego z domyślną <xref:System.ServiceModel.WSHttpBinding> (wartość domyślna <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, która jest <xref:System.ServiceModel.SecurityMode.Message>), wszystkie komunikaty są zaszyfrowana i podpisana, ponieważ jest to domyślny poziom ochrony. Jednakże, gdy `ISampleService` domyślnie jest używana usługa <xref:System.ServiceModel.BasicHttpBinding> (wartość domyślna <xref:System.ServiceModel.SecurityMode>, co jest <xref:System.ServiceModel.SecurityMode.None>), wszystkie komunikaty są wysyłane jako tekst, ponieważ nie istnieje żadne dodatkowe zabezpieczenia dla tego powiązania w związku z czym poziom ochrony jest ignorowany (oznacza to, komunikaty nie są szyfrowane ani podpisany). Jeśli <xref:System.ServiceModel.SecurityMode> została zmieniona na <xref:System.ServiceModel.SecurityMode.Message>, a następnie te komunikaty czy zaszyfrowana i podpisana za (ponieważ teraz wyniesie powiązania domyślnego poziomu ochrony).  
  
 Jeśli chcesz jawnie określić lub Dostosuj wymagań dotyczących ochrony dla umowy, ustaw <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> właściwości (lub dowolnym `ProtectionLevel` właściwości w zakresie mniejszych) do poziomu wymaga umowy serwisowej. W takim przypadku jawne ustawienie wymaga powiązania obsługę tego ustawienia co najmniej zakres używany. Na przykład poniższy przykład kodu Określa jedną <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> wartości jawnie, dla `GetGuid` operacji.  
  
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
  
 Poniżej znajduje się równoważne kodu języka Visual Basic.  
  
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
  
 Usługa, która implementuje to `IExplicitProtectionLevelSampleService` kontraktu i ma punktu końcowego, który używa domyślnej <xref:System.ServiceModel.WSHttpBinding> (wartość domyślna <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, która jest <xref:System.ServiceModel.SecurityMode.Message>) ma następującą charakterystykę:  
  
-   `GetString` Operacji wiadomości są zaszyfrowana i podpisana.  
  
-   `GetInt` Operacji komunikaty są wysyłane w postaci niezaszyfrowanej i bez znaku (to znaczy, gładkie) tekst.  
  
-   `GetGuid` Operacji <xref:System.Guid?displayProperty=nameWithType> jest zwracana w komunikacie, który jest zaszyfrowana i podpisana.  
  
 Aby uzyskać więcej informacji na temat poziomów ochrony i sposobu ich używania, zobacz [poziom ochrony opis](../../../docs/framework/wcf/understanding-protection-level.md). Aby uzyskać więcej informacji o zabezpieczeniach, zobacz [zabezpieczania usług](../../../docs/framework/wcf/securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Wymagania dotyczące innych operacji podpisu  
 Niektóre funkcje aplikacji wymagają określonego rodzaju operacji podpisu. Na przykład <xref:System.ServiceModel.NetMsmqBinding> powiązanie obsługuje trwałe usług i klientów, w których aplikację można uruchomić ponownie w trakcie komunikacji i uruchomienia instalacji którym ją przerwał pracę bez Brak komunikaty. (Aby uzyskać więcej informacji, zobacz [kolejki programu WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).) Jednak operacje trwałe należy wykonać tylko jedną `in` parametrów i nie zwraca wartości.  
  
 Innym przykładem jest użycie <xref:System.IO.Stream> typów podczas wykonywania operacji. Ponieważ <xref:System.IO.Stream> parametr zawiera treść cały komunikat, jeśli danych wejściowych lub wyjściowych (oznacza to, `ref` parametru `out` parametrów lub wartości zwracanej) jest typu <xref:System.IO.Stream>, to musi być tylko danych wejściowych lub wyjściowych określone w sieci Operacja. Ponadto, parametr lub typ zwracany musi być równa albo <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>, lub <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>. Aby uzyskać więcej informacji na temat strumieni, zobacz [duże ilości danych i przesyłania strumieniowego](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Nazwy i przestrzenie nazw oraz zaciemnienie  
 Nazwy i przestrzenie nazw typów .NET w definicji operacji i kontrakty są istotne podczas kontrakty są konwertowane na WSDL i tworzonych i wysyłanych komunikatów kontraktu. W związku z tym zdecydowanie zaleca się że nazwy kontraktu usługi i przestrzenie nazw są jawnie ustawione za pomocą `Name` i `Namespace` właściwości pomocniczych wszystkie kontraktu atrybutów, takich jak <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>,  <xref:System.Runtime.Serialization.DataMemberAttribute>i inne atrybuty kontraktu.  
  
 Jeden wynik jest, że jeśli nazwy i przestrzenie nazw nie jest jawnie ustawiona, użycie zaciemnienie IL w zestawie zmienia nazwy typów kontraktu i obszary nazw i powoduje modyfikacji WSDL oraz wymiany danych przesyłanych w sieci, które nie są zwykle. Jeśli nie ustawiaj nazwy kontraktu i przestrzenie nazw jawnie, ale ma zostać użyta zaciemnienie, użyj <xref:System.Reflection.ObfuscationAttribute> i <xref:System.Reflection.ObfuscateAssemblyAttribute> atrybutów, aby zapobiec zmiana Umowy wpisz nazwy i przestrzenie nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie kontraktu „żądanie-odpowiedź”](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)  
 [Instrukcje: tworzenie kontraktu jednokierunkowego](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)  
 [Instrukcje: tworzenie kontraktu dwukierunkowego](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Określanie transferu danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 [Określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Korzystanie z sesji](../../../docs/framework/wcf/using-sessions.md)  
 [Operacje synchroniczne i asynchroniczne](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)  
 [Niezawodne usługi](../../../docs/framework/wcf/reliable-services.md)  
 [Usługi i transakcje](../../../docs/framework/wcf/services-and-transactions.md)
