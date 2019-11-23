---
title: Projektowanie kontraktów usług
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 27f867bbf079c2e202d93425ddb951fc0df7784a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318380"
---
# <a name="designing-service-contracts"></a>Projektowanie kontraktów usług
W tym temacie opisano kontrakty usługi, sposób ich definiowania, dostępne operacje (oraz implikacje wymiany komunikatów), typy danych, które są używane, a także inne problemy, które ułatwiają projektowanie operacji, które spełniają wymagania związane z Twoim scenariuszem.  
  
## <a name="creating-a-service-contract"></a>Tworzenie kontraktu usługi  
 Usługi uwidaczniają wiele operacji. W aplikacjach Windows Communication Foundation (WCF) Zdefiniuj operacje, tworząc metodę i oznaczając ją atrybutem <xref:System.ServiceModel.OperationContractAttribute>. Następnie, aby utworzyć kontrakt usługi, należy zgrupować wszystkie operacje, deklarując je w interfejsie oznaczonym atrybutem <xref:System.ServiceModel.ServiceContractAttribute> lub definiując je w klasie oznaczonej przy użyciu tego samego atrybutu. (Aby uzyskać podstawowy przykład, zobacz [How to: define a Service Contract](how-to-define-a-wcf-service-contract.md).)  
  
 Wszelkie metody, które nie mają atrybutu <xref:System.ServiceModel.OperationContractAttribute>, nie są operacjami usługi i nie są udostępniane przez usługi WCF.  
  
 W tym temacie opisano następujące kwestie decyzyjne podczas projektowania kontraktu usługi:  
  
- Określa, czy mają być używane klasy czy interfejsy.  
  
- Jak określić typy danych, które mają być wymieniane.  
  
- Typy wzorców programu Exchange, których można użyć.  
  
- Czy można wprowadzać jawne wymagania dotyczące zabezpieczeń części kontraktu.  
  
- Ograniczenia dotyczące danych wejściowych i wyjściowych operacji.  
  
## <a name="classes-or-interfaces"></a>Klasy lub interfejsy  
 Zarówno klasy, jak i interfejsy reprezentują grupowanie funkcji, w związku z czym obie mogą służyć do definiowania kontraktu usługi WCF. Zaleca się jednak korzystanie z interfejsów, ponieważ umożliwiają one bezpośrednie modelowanie kontraktów usług. Bez implementacji interfejsy nie więcej niż definiują grupowanie metod z określonymi podpisami. Zaimplementuj interfejs kontraktu usługi i zaimplementowano usługę WCF.  
  
 Wszystkie zalety interfejsów zarządzanych mają zastosowanie do interfejsów kontraktu usługi:  
  
- Interfejsy kontraktu usługi mogą rozszerać dowolną liczbę innych interfejsów kontraktu usługi.  
  
- Pojedyncza Klasa może implementować dowolną liczbę kontraktów usług, implementując te interfejsy kontraktu usługi.  
  
- Implementację kontraktu usługi można zmodyfikować, zmieniając implementację interfejsu, natomiast kontrakt usługi pozostaje taki sam.  
  
- Możesz uzyskać wersję usługi, implementując stary interfejs i nowy. Stara klienci łączą się z wersją oryginalną, a nowsze klienci mogą łączyć się z nowszą wersją.  
  
> [!NOTE]
> W przypadku dziedziczenia z innych interfejsów kontraktu usług nie można przesłonić właściwości operacji, takich jak nazwa lub przestrzeń nazw. Jeśli podjęto próbę wykonania tej czynności, należy utworzyć nową operację w bieżącym kontrakcie usługi.  
  
 Przykład użycia interfejsu do tworzenia kontraktu usługi zawiera temat [jak: Tworzenie usługi przy użyciu interfejsu kontraktu](./feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Można jednak użyć klasy w celu zdefiniowania kontraktu usługi i wdrożenia tego kontraktu w tym samym czasie. Zaletą tworzenia usług przez zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> bezpośrednio do klasy oraz metod na klasie, jest to szybkość i prostota. Wadą są te, których klasy zarządzane nie obsługują wielokrotnego dziedziczenia, a w związku z tym w danym momencie można zaimplementować tylko jeden kontrakt usługi. Ponadto jakakolwiek modyfikacja sygnatury klasy lub metody modyfikuje publiczny kontrakt dla tej usługi, co może uniemożliwić niezmodyfikowanym klientom korzystanie z usługi. Aby uzyskać więcej informacji, zobacz [implementowanie kontraktów usług](implementing-service-contracts.md).  
  
 Aby zapoznać się z przykładem, który używa klasy do tworzenia kontraktu usługi i implementowania go w tym samym czasie, zobacz [How to: Create a Service with a Contract Class](./feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 W tym momencie należy zrozumieć różnicę między definiowaniem kontraktu usługi przy użyciu interfejsu i przy użyciu klasy. Następnym krokiem jest podjęcie decyzji o tym, jakie dane mogą być przesyłane z powrotem do usługi i jej klientów.  
  
## <a name="parameters-and-return-values"></a>Parametry i wartości zwracane  
 Każda operacja ma wartość zwracaną i parametr, nawet jeśli są one `void`. Jednak w przeciwieństwie do metody lokalnej, w której można przekazać odwołania do obiektów z jednego obiektu do drugiego, operacje usługi nie przechodzą odwołań do obiektów. Zamiast tego przechodzą kopie obiektów.  
  
 Jest to istotne, ponieważ każdy typ używany w parametrze lub wartości zwracanej musi być możliwy do serializacji. oznacza to, że musi być możliwe przekonwertowanie obiektu tego typu na strumień bajtów i ze strumienia bajtów do obiektu.  
  
 Typy pierwotne są domyślnie serializowane, tak jak wiele typów w .NET Framework.  
  
> [!NOTE]
> Wartość nazw parametrów w podpisie operacji jest częścią kontraktu i jest uwzględniana wielkość liter. Jeśli chcesz używać tej samej nazwy parametru lokalnie, ale zmodyfikuj nazwę w opublikowanych metadanych, zapoznaj się z <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.  
  
#### <a name="data-contracts"></a>Kontrakty danych  
 Aplikacje zorientowane na usługę, takie jak aplikacje Windows Communication Foundation (WCF), są przeznaczone do współpracy z szeroką możliwą liczbą aplikacji klienckich na platformach firmy Microsoft i innych firm. W celu uzyskania szerokiej możliwości współdziałania zaleca się oznaczenie typów przy użyciu atrybutów <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> w celu utworzenia kontraktu danych, który stanowi część kontraktu usługi opisującego dane, które są używane przez operacje usługi.  
  
 Kontrakty danych są umowami dotyczącymi stylu zgody: żaden typ lub składowa danych nie jest serializowany, chyba że jawnie zastosowano atrybut kontraktu danych. Kontrakty danych są niepowiązane z zakresem dostępu zarządzanego kodu: prywatne składowe danych mogą być serializowane i wysyłane w innym miejscu, aby można było uzyskać do nich dostęp publicznie. (Aby zapoznać się z podstawowym przykładem kontraktu danych, zobacz [How to: Create a Basic Data Contract for a Class or Structure](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) Usługa WCF obsługuje definicje podstawowych komunikatów SOAP, które umożliwiają działanie tej operacji, a także serializacji typów danych do i z treści komunikatów. Dopóki Twoje typy danych są serializowane, nie trzeba myśleć o podstawowej infrastrukturze wymiany komunikatów podczas projektowania operacji.  
  
 Chociaż Typowa aplikacja WCF używa atrybutów <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> do tworzenia kontraktów danych dla operacji, można użyć innych mechanizmów serializacji. Standardowe <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> i <xref:System.Xml.Serialization.IXmlSerializable> mechanizmy obsługują Serializacja typów danych do bazowych komunikatów protokołu SOAP, które przenoszą je z jednej aplikacji na inną. Jeśli typy danych wymagają specjalnej pomocy, można zastosować więcej strategii serializacji. Aby uzyskać więcej informacji na temat opcji serializacji typów danych w aplikacjach WCF, zobacz [określanie transfer danych w kontraktach usług](./feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Mapowanie parametrów i zwracanie wartości na wymianę komunikatów  
 Operacje usługi są obsługiwane przez podstawową wymianę komunikatów protokołu SOAP, które przesyłają dane aplikacji z powrotem i do przodu, a także do danych wymaganych przez aplikację w celu obsługi pewnych standardowych funkcji zabezpieczeń, transakcji i związanych z sesją. Ponieważ jest to przypadek, sygnatura operacji usługi wymusza określony podstawowy *wzorzec wymiany komunikatów* (unikatowy MEP), który może obsługiwać transfer danych i funkcje wymagane przez operację. W modelu programowania WCF można określić trzy wzorce: żądania/odpowiedzi, jednokierunkowe i dupleksowe wzorce wiadomości.  
  
##### <a name="requestreply"></a>Żądanie/odpowiedź  
 Wzorzec żądania/odpowiedzi to jeden, w którym nadawca żądania (aplikacja kliencka) odbiera odpowiedź, z którą żądanie jest skorelowane. Jest to domyślny unikatowy MEP, ponieważ obsługuje operację, w której jeden lub więcej parametrów jest przenoszona do operacji, a zwracana wartość jest przenoszona z powrotem do obiektu wywołującego. Poniższy C# przykład kodu pokazuje podstawową operację usługi, która przyjmuje jeden ciąg i zwraca ciąg.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Poniżej znajduje się odpowiedni kod Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Ta sygnatura operacji określa formę wymiany komunikatów źródłowych. Jeśli nie istniała żadna korelacja, platforma WCF nie może określić, dla której operacji jest zamierzona wartość zwracana.  
  
 Należy pamiętać, że jeśli nie określisz innego podstawowego wzorca komunikatów, nawet operacje usługi, które zwracają `void` (`Nothing` w Visual Basic) są wymianami komunikatów żądania/odpowiedzi. Wynik operacji polega na tym, że jeśli klient nie wywoła operacji asynchronicznie, klient przestanie być przetwarzany do momentu odebrania komunikatu zwrotnego, nawet jeśli ten komunikat jest pusty w normalnym przypadku. Poniższy C# przykład kodu pokazuje operację, która nie zwraca, dopóki klient nie otrzyma pustego komunikatu w odpowiedzi.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Poniżej znajduje się odpowiedni kod Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 Powyższy przykład może spowalniać wydajność i czas odpowiedzi klienta, jeśli wykonanie operacji trwa długo, ale istnieją zalety operacji żądania/odpowiedzenia, nawet gdy zwracają `void`. Najbardziej oczywiste jest, że błędy protokołu SOAP mogą być zwracane w komunikacie odpowiedzi, co oznacza, że wystąpił jakiś warunek błędu związany z usługą, zarówno w komunikacji, jak i przetwarzaniu. Błędy protokołu SOAP, które są określone w kontrakcie usługi, są przesyłane do aplikacji klienckiej jako obiekt <xref:System.ServiceModel.FaultException%601>, gdzie parametr typu jest typem określonym w kontrakcie usługi. Powoduje to powiadomienie klientów o błędach w usługach WCF. Aby uzyskać więcej informacji o wyjątkach, błędach SOAP i obsłudze błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](specifying-and-handling-faults-in-contracts-and-services.md). Aby zapoznać się z przykładem usługi żądania/odpowiedzi i klienta, zobacz [How to: Create a Request-Reply kontraktu](./feature-details/how-to-create-a-request-reply-contract.md). Aby uzyskać więcej informacji o problemach z wzorcem żądanie-odpowiedź, zobacz [usługi żądanie-odpowiedź](./feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Jednokierunkowe  
 Jeśli klient aplikacji usługi WCF nie powinien czekać na ukończenie operacji i nie przetwarza błędów protokołu SOAP, operacja może określić wzorzec komunikatu jednokierunkowego. Operacja jednokierunkowa polega na tym, że klient wywołuje operację i kontynuuje przetwarzanie, gdy WCF zapisuje komunikat w sieci. Zazwyczaj oznacza to, że jeśli dane wysyłane w wiadomości wychodzącej nie są niezwykle duże, klient nadal działa niemal natychmiast (chyba że wystąpi błąd podczas wysyłania danych). Ten typ wzorca komunikatów programu Exchange obsługuje zachowanie podobne do zdarzeń z klienta do aplikacji usługi.  
  
 Nie można obsługiwać wymiany komunikatów, w której jest wysyłany jeden komunikat, a żadna z nich nie jest obsługiwana w przypadku operacji usługi, która określa wartość zwracaną inną niż `void`; w takim przypadku zostanie zgłoszony wyjątek <xref:System.InvalidOperationException>.  
  
 Komunikat zwrotny nie oznacza także, że nie można zwrócić błędu protokołu SOAP w celu wskazania błędów w przetwarzaniu lub komunikacji. (Przekazywanie informacji o błędach, gdy operacje są operacją jednokierunkową, wymaga wzorca wymiany komunikatów dupleksowych).  
  
 Aby określić jednokierunkową wymianę komunikatów dla operacji, która zwraca `void`, ustaw właściwość <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> na `true`, jak w poniższym C# przykładzie kodu.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Poniżej znajduje się odpowiedni kod Visual Basic.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Ta metoda jest identyczna z poprzednim przykładem żądania/odpowiedzi, ale ustawienie właściwości <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> na `true` oznacza, że mimo że metoda jest taka sama, operacja usługi nie wysyła komunikatu zwrotnego, a klienci zwracają natychmiast po przekazaniu komunikatu wychodzącego do warstwy kanału. Aby zapoznać się z przykładem, zobacz [How to: Create](./feature-details/how-to-create-a-one-way-contract.md)an jednokierunkowe kontraktu. Aby uzyskać więcej informacji na temat wzorca jednokierunkowego, zobacz jednokierunkowe [usługi](./feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Dupleks  
 Wzorzec dupleksu jest scharakteryzowany przez zdolność komunikacji między usługą i klientem niezależnie od tego, czy jest używana wiadomość jednokierunkowa, czy żądanie/odpowiedź. Ta forma komunikacji dwukierunkowej jest przydatna w przypadku usług, które muszą komunikować się bezpośrednio z klientem lub w celu zapewnienia asynchronicznego środowiska po obu stronach wymiany komunikatów, w tym zachowania podobne do zdarzeń.  
  
 Wzorzec dupleksu jest nieco bardziej skomplikowany niż wzorce żądania/odpowiedzi lub jednokierunkowe jednokierunkowo ze względu na dodatkowy mechanizm komunikacji z klientem.  
  
 Aby zaprojektować umowę dupleksową, należy również zaprojektować kontrakt wywołania zwrotnego i przypisać typ tego kontraktu wywołania zwrotnego do właściwości <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> atrybutu <xref:System.ServiceModel.ServiceContractAttribute>, który oznacza kontrakt usługi.  
  
 Aby zaimplementować wzorzec dupleks, należy utworzyć drugi interfejs, który zawiera deklaracje metody, które są wywoływane na kliencie.  
  
 Aby zapoznać się z przykładem tworzenia usługi i klienta, który uzyskuje dostęp do tej usługi, zobacz [How to: Create an Duplex kontraktu](./feature-details/how-to-create-a-duplex-contract.md) i [instrukcje: dostęp do usług za pomocą kontraktu dupleksowego](./feature-details/how-to-access-services-with-a-duplex-contract.md). Aby uzyskać przykład roboczy, zobacz [Duplex](./samples/duplex.md). Aby uzyskać więcej informacji o problemach z używaniem umów dupleksowych, zobacz [usługi dupleksowe](./feature-details/duplex-services.md).  
  
> [!CAUTION]
> Gdy usługa otrzymuje komunikat o dupleksie, przegląda element `ReplyTo` w tym komunikacie przychodzącym, aby określić, gdzie należy wysłać odpowiedź. Jeśli kanał używany do odbierania wiadomości nie jest zabezpieczony, niezaufany klient może wysłać złośliwą wiadomość z `ReplyTo`maszyny docelowej, co prowadzi do ataku typu "odmowa usługi" (DOS) tej maszyny docelowej.  
  
##### <a name="out-and-ref-parameters"></a>Parametry out i ref  
 W większości przypadków można użyć parametrów `in` (`ByVal` w Visual Basic) i `out` i `ref` parametrów (`ByRef` w Visual Basic). Ponieważ oba parametry `out` i `ref` wskazują, że dane są zwracane z operacji, sygnatura operacji, taka jak poniżej, określa, że operacja żądania/odpowiedzi jest wymagana, nawet jeśli sygnatura operacji zwróci `void`.  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 Poniżej znajduje się odpowiedni kod Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 Jedynymi wyjątkami są te przypadki, w których podpis ma określoną strukturę. Na przykład można użyć powiązania <xref:System.ServiceModel.NetMsmqBinding>, aby komunikować się z klientami tylko wtedy, gdy metoda używana do deklarowania operacji zwraca `void`; nie może istnieć wartość wyjściowa, niezależnie od tego, czy jest to wartość zwracana, `ref`czy `out` parametr.  
  
 Ponadto przy użyciu parametrów `out` lub `ref` wymaga, aby operacja zawierała podstawowy komunikat odpowiedzi na potrzeby przywrócenia zmodyfikowanego obiektu. Jeśli operacja jest operacją jednokierunkową, wyjątek <xref:System.InvalidOperationException> jest generowany w czasie wykonywania.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Określ poziom ochrony wiadomości dla kontraktu  
 Podczas projektowania kontraktu należy również określić poziom ochrony wiadomości dla usług, które implementują kontrakt. Jest to konieczne tylko wtedy, gdy zabezpieczenia wiadomości są stosowane do powiązania w punkcie końcowym kontraktu. Jeśli powiązanie ma wyłączone zabezpieczenia (oznacza to, że jeśli powiązanie dostarczone z systemem ustawia <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> na wartość <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>), nie trzeba decydować o poziomie ochrony wiadomości dla kontraktu. W większości przypadków powiązania dostarczone przez system z zabezpieczeniami na poziomie komunikatów mają wystarczający poziom ochrony i nie trzeba uwzględniać poziomu ochrony dla każdej operacji lub dla każdego komunikatu.  
  
 Poziom ochrony to wartość określająca, czy komunikaty (lub części komunikatów) obsługujące usługę są podpisane, podpisane i szyfrowane lub wysyłane bez podpisu lub szyfrowania. Poziom ochrony można ustawić w różnych zakresach: na poziomie usługi, dla konkretnej operacji, dla komunikatu w ramach tej operacji lub w części komunikatu. Wartości ustawione w jednym zakresie stają się wartością domyślną dla mniejszych zakresów, chyba że zostaną jawnie zastąpione. Jeśli konfiguracja powiązania nie może zapewnić wymaganego minimalnego poziomu ochrony dla kontraktu, zgłaszany jest wyjątek. W przypadku niejawnego ustawiania wartości poziomu ochrony w ramach kontraktu Konfiguracja powiązania steruje poziomem ochrony dla wszystkich komunikatów, Jeśli powiązanie ma zabezpieczenia komunikatów. To zachowanie domyślne.  
  
> [!IMPORTANT]
> Decydując, czy w sposób jawny ustawiać różne zakresy kontraktu do wartości mniejszej niż pełny poziom ochrony <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> jest to ogólnie podejmowana decyzja, która stanowi wymiana pewnego stopnia bezpieczeństwa w celu zwiększenia wydajności. W takich przypadkach decyzje muszą obejść między operacjami i wartość danych wymienianych przez te osoby. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie usług](securing-services.md).  
  
 Na przykład poniższy przykład kodu nie ustawia właściwości <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> ani <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> dla kontraktu.  
  
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
  
 Poniżej znajduje się odpowiedni kod Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 Podczas współdziałania z implementacją `ISampleService` w punkcie końcowym z domyślną <xref:System.ServiceModel.WSHttpBinding> (domyślny <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, który jest <xref:System.ServiceModel.SecurityMode.Message>), wszystkie komunikaty są szyfrowane i podpisywane, ponieważ jest to domyślny poziom ochrony. Jeśli jednak usługa `ISampleService` jest używana z domyślną <xref:System.ServiceModel.BasicHttpBinding> (domyślnie <xref:System.ServiceModel.SecurityMode>, która jest <xref:System.ServiceModel.SecurityMode.None>), wszystkie komunikaty są wysyłane jako tekst, ponieważ nie ma żadnych zabezpieczeń dla tego powiązania i dlatego poziom ochrony jest ignorowany (oznacza to, że komunikaty nie są szyfrowane ani podpisywane). Jeśli <xref:System.ServiceModel.SecurityMode> został zmieniony na <xref:System.ServiceModel.SecurityMode.Message>, te komunikaty byłyby szyfrowane i podpisane (ponieważ teraz będzie to domyślny poziom ochrony powiązań).  
  
 Jeśli chcesz jawnie określić lub dostosować wymagania dotyczące ochrony dla danego kontraktu, ustaw właściwość <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> (lub dowolne właściwości `ProtectionLevel` w mniejszym zakresie) na poziom wymagany przez kontrakt usługi. W takim przypadku użycie ustawienia jawnego wymaga powiązania do obsługi tego ustawienia na poziomie minimalnym dla użytego zakresu. Na przykład poniższy przykład kodu określa jedną wartość <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> jawnie dla operacji `GetGuid`.  
  
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
  
 Poniżej znajduje się odpowiedni kod Visual Basic.  
  
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
  
 Usługa implementująca ten `IExplicitProtectionLevelSampleService` kontrakt i ma punkt końcowy, który używa domyślnego <xref:System.ServiceModel.WSHttpBinding> (domyślny <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, który jest <xref:System.ServiceModel.SecurityMode.Message>), ma następujące zachowanie:  
  
- Komunikaty `GetString` operacji są szyfrowane i podpisane.  
  
- Komunikaty `GetInt` operacji są wysyłane jako nieszyfrowane i niepodpisane (zwykły) tekst.  
  
- <xref:System.Guid?displayProperty=nameWithType> operacji `GetGuid` jest zwracana w zaszyfrowanym i podpisanym komunikacie.  
  
 Aby uzyskać więcej informacji o poziomach ochrony i sposobach ich użycia, zobacz [Opis poziomu ochrony](understanding-protection-level.md). Aby uzyskać więcej informacji na temat zabezpieczeń, zobacz [Zabezpieczanie usług](securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Inne wymagania dotyczące podpisu operacji  
 Niektóre funkcje aplikacji wymagają podpisu określonego rodzaju operacji. Na przykład powiązanie <xref:System.ServiceModel.NetMsmqBinding> obsługuje trwałe usługi i klientów, w których aplikacja może zostać ponownie uruchomiona w trakcie komunikacji i wyłączać się w miejscu, w którym została pozostawiona bez żadnych komunikatów. (Aby uzyskać więcej informacji, zobacz [kolejki w programie WCF](./feature-details/queues-in-wcf.md)). Jednak operacje trwałe muszą przyjmować tylko jeden `in` parametr i nie mają wartości zwracanej.  
  
 Innym przykładem jest użycie typów <xref:System.IO.Stream> w operacjach. Ponieważ parametr <xref:System.IO.Stream> zawiera całą treść wiadomości, jeśli dane wejściowe lub wyjściowe (czyli parametr `ref`, `out` parametr lub wartość zwracana) są typu <xref:System.IO.Stream>, wówczas musi to być jedyne dane wejściowe lub wyjściowe określone w operacji. Ponadto parametr lub typ zwracany muszą mieć wartość <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>lub <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>. Aby uzyskać więcej informacji o strumieniach, zobacz artykuł [duże ilości danych i przesyłanie strumieniowe](./feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Nazwy, przestrzenie nazw i zaciemnianie  
 Nazwy i przestrzenie nazw typów .NET w definicji kontraktów i operacji są istotne w przypadku, gdy kontrakty są konwertowane do języka WSDL i gdy wiadomości kontraktu są tworzone i wysyłane. Dlatego zdecydowanie zaleca się, aby nazwy i przestrzenie nazw kontraktu usług były jawnie ustawiane przy użyciu właściwości `Name` i `Namespace` wszystkich atrybutów kontraktu pomocniczego, takich jak <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.Runtime.Serialization.DataMemberAttribute>i inne atrybuty kontraktu.  
  
 W związku z tym, jeśli nazwy i przestrzenie nazw nie są jawnie ustawione, użycie elementu zaciemniania IL na zestawie zmienia nazwy typów kontraktu i przestrzenie nazw i skutkuje zmodyfikowaniem danych WSDL i szkieletowych, które zwykle kończą się niepowodzeniem. Jeśli nie ustawisz jawnie nazw kontraktu i przestrzeni nazw, ale zamierzasz używać zaciemniania, użyj atrybutów <xref:System.Reflection.ObfuscationAttribute> i <xref:System.Reflection.ObfuscateAssemblyAttribute>, aby zapobiec modyfikowaniu nazw typów kontraktu i przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie kontraktu „żądanie-odpowiedź”](./feature-details/how-to-create-a-request-reply-contract.md)
- [Instrukcje: tworzenie kontraktu jednokierunkowego](./feature-details/how-to-create-a-one-way-contract.md)
- [Instrukcje: tworzenie kontraktu dwukierunkowego](./feature-details/how-to-create-a-duplex-contract.md)
- [Określanie transferu danych w kontraktach usług](./feature-details/specifying-data-transfer-in-service-contracts.md)
- [Określanie i obsługa błędów w kontraktach i usługach](specifying-and-handling-faults-in-contracts-and-services.md)
- [Korzystanie z sesji](using-sessions.md)
- [Operacje synchroniczne i asynchroniczne](synchronous-and-asynchronous-operations.md)
- [Niezawodne usługi](reliable-services.md)
- [Usługi i transakcje](services-and-transactions.md)
