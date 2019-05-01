---
title: Tworzenie wiązań zdefiniowanych przez użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 54a1c8e06991729ea8556d82d31897c522f6d173
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923243"
---
# <a name="creating-user-defined-bindings"></a>Tworzenie wiązań zdefiniowanych przez użytkownika
Istnieje kilka sposobów tworzenia powiązania nie został dostarczony przez system:  
  
- Tworzenie niestandardowego powiązania, na podstawie <xref:System.ServiceModel.Channels.CustomBinding> klasy, która jest kontenerem, który można wypełnić elementy powiązania. Niestandardowe powiązanie jest dodawane do punktu końcowego usługi. Można utworzyć niestandardowego powiązania, które albo programowo, albo w konfiguracji aplikacji pliku. Aby użyć elementu powiązania z pliku konfiguracji aplikacji, element powiązania musi rozszerzać <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. Aby uzyskać więcej informacji na temat powiązania niestandardowej zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md) i <xref:System.ServiceModel.Channels.CustomBinding>.  
  
- Można utworzyć klasę, która pochodzi od standardowego powiązania. Na przykład można wyprowadzić klasę z <xref:System.ServiceModel.WSHttpBinding> i zastąpić <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> metodę, aby uzyskać elementy powiązania i Wstaw element niestandardowego powiązania lub określenia konkretnej wartości dotyczące zabezpieczeń.  
  
- Można utworzyć nową <xref:System.ServiceModel.Channels.Binding> typu na całkowitą kontrolę wykonania całego powiązania.  
  
## <a name="the-order-of-binding-elements"></a>Kolejność elementów wiązania  
 Każdy element powiązania reprezentuje krok przetwarzania podczas wysyłania lub odbierania komunikatów. W czasie wykonywania elementy powiązania Tworzenie kanałów i odbiorników niezbędne do utworzenia stosów kanałów przychodzących i wychodzących.  
  
 Istnieją trzy główne typy elementy powiązania: Protokół powiązania elementów, kodowania elementów powiązania i elementy powiązania transportu.  
  
 Elementy powiązania protokołu — te elementy reprezentują kroki przetwarzania wyższego poziomu, które działają w wiadomości. Kanałów i odbiorników utworzone przez te elementy powiązania można dodać, usunąć lub zmodyfikować zawartości komunikatu. Podane powiązanie może mieć dowolną liczbę elementów powiązania protokołu, każdy dziedziczenie z <xref:System.ServiceModel.Channels.BindingElement>. Windows Communication Foundation (WCF) obejmuje kilka elementów powiązania protokołu, w tym <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> i <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
 Kodowanie elementu powiązania — reprezentują one elementy przekształcenia między wiadomość i kodowania gotowe do transmisji w sieci. Typowe powiązania WCF zawierać dokładnie jeden element powiązania kodowania. Kodowanie elementów wiązania przykłady <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>i <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Jeśli kodowanie elementu powiązania nie zostanie określony dla powiązania, domyślnym kodowaniem jest używany. W przypadku transportu HTTP i danych binarnych w przeciwnym razie, wartość domyślna to text.  
  
 Element powiązania transportu — te elementy reprezentują transmisji kodowania komunikatu protokołu transportu. Typowe powiązania WCF zawierać dokładnie jeden element powiązania transportu, która dziedziczy z <xref:System.ServiceModel.Channels.TransportBindingElement>. Przykłady elementów wiązania transportu <xref:System.ServiceModel.Channels.TcpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement>i <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>.  
  
 Podczas tworzenia nowego powiązania ważna jest kolejność elementów dodanych wiązania. Zawsze dodawaj elementy powiązania w następującej kolejności:  
  
|Warstwa|Opcje|Wymagane|  
|-----------|-------------|--------------|  
|Przepływ transakcji|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Nie|  
|Niezawodność|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Nie|  
|Zabezpieczenia|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Nie|  
|Złożone komunikacja dwukierunkowa|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Nie|  
|Kodowanie|Tekst, Binary MTOM, niestandardowe|Tak*|  
|Transport|TCP i nazwane potoki, HTTP, HTTPS, usługa MSMQ, niestandardowe|Yes|  
  
 * Ponieważ jest wymagane kodowanie dla każdego powiązania, jeśli nie określono kodowania, WCF dodaje domyślne kodowanie dla Ciebie. Wartość domyślna to Text/XML binarnej i dla transportu HTTP i HTTPS, w przeciwnym razie.  
  
## <a name="creating-a-new-binding-element"></a>Tworzenie nowego elementu powiązania  
 Oprócz typów pochodnych typu <xref:System.ServiceModel.Channels.BindingElement> , które są wprowadzone przez architekturę WCF, możesz utworzyć własne elementy powiązania. Dzięki temu można dostosować sposób stosu powiązania jest tworzony i składniki, które bardziej szczegółowo w nim, tworząc własne <xref:System.ServiceModel.Channels.BindingElement> może być składana przy użyciu innych typów dostarczanych przez system w stosie.  
  
 Na przykład w przypadku zaimplementowania `LoggingBindingElement` zapewniającej możliwość rejestrowania komunikatu do bazy danych, należy go umieścić powyżej kanał transportu w stosie kanału. W takim przypadku aplikacja tworzy niestandardowego powiązania, które składa się `LoggingBindingElement` z `TcpTransportBindingElement`, jak w poniższym przykładzie.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 Jak zapisać nowy element powiązania, zależy od jego dokładne działanie. Jednym z przykładów, [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md), zawiera szczegółowy opis sposobu implementacji jeden rodzaj elementu powiązania.  
  
## <a name="creating-a-new-binding"></a>Tworzenie nowego powiązania  
 Element powiązania utworzone przez użytkownika może służyć na dwa sposoby. Poprzedniej sekcji przedstawiono sposób pierwszy: za pomocą niestandardowego powiązania. Powiązanie niestandardowe umożliwia użytkownikowi tworzenie własnych powiązania na podstawie dowolnego zestawu powiązania elementów, w tym te utworzone przez użytkownika.  
  
 Jeśli używasz powiązania w więcej niż jedną aplikację, utworzyć własne powiązania i rozszerzanie <xref:System.ServiceModel.Channels.Binding>. Pozwala to uniknąć ręcznego tworzenia niestandardowego powiązania za każdym razem, gdy chcesz z niego korzystać. Powiązania zdefiniowane przez użytkownika umożliwia definiowanie zachowania wiązania i obejmują elementy powiązań zdefiniowanych przez użytkownika. I jest *wstępnie spakowane*: nie trzeba odbudować powiązania, za każdym razem, gdy ich używania.  
  
 Co najmniej powiązania zdefiniowane przez użytkownika muszą implementować <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metody i <xref:System.ServiceModel.Channels.Binding.Scheme%2A> właściwości.  
  
 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> Metoda zwraca nowy <xref:System.ServiceModel.Channels.BindingElementCollection> zawierającą elementy wiązania dla wiązania. Kolekcja jest określona i może zawierać elementy powiązania protokołu najpierw, następuje kodowania element powiązania, a następnie element powiązania transportu. Podczas korzystania z elementów wiązania WCF dostarczane przez system, należy wykonać element powiązania, kolejność reguł określonych w [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md). Ta kolekcja nigdy nie powinien odwoływać się do obiektów w klasie powiązań zdefiniowanych przez użytkownika; odwoływać się do w związku z tym, autorzy powiązania musi zwracać `Clone()` z <xref:System.ServiceModel.Channels.BindingElementCollection> przy każdym wywołaniu <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>.  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> Właściwość reprezentuje schemat identyfikatora URI protokołu transportowego używany w wiązaniu. Na przykład *WSHttpBinding* i *NetTcpBinding* zwracać "http" i "net.tcp" z odpowiednich <xref:System.ServiceModel.Channels.Binding.Scheme%2A> właściwości.  
  
 Aby uzyskać pełną listę opcjonalny metody i właściwości dla powiązań zdefiniowanych przez użytkownika, zobacz <xref:System.ServiceModel.Channels.Binding>.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie implementuje powiązanie profilu w `SampleProfileUdpBinding`, która jest pochodną <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` Zawiera maksymalnie cztery elementy powiązania w niej: jeden użytkownik utworzył `UdpTransportBindingElement`; i trzy dostarczane przez system: `TextMessageEncodingBindingElement`, `CompositeDuplexBindingElement`, i `ReliableSessionBindingElement`.  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
## <a name="security-restrictions-with-duplex-contracts"></a>Ograniczenia zabezpieczeń za pomocą kontrakty dwukierunkowe  
 Nie wszystkie elementy powiązania są ze sobą zgodne. W szczególności istnieją pewne ograniczenia dotyczące zabezpieczeń elementy wiązania, gdy jest używane z kontrakty dwukierunkowe.  
  
### <a name="one-shot-security"></a>Jednorazowej zabezpieczeń  
 Możesz zaimplementować zabezpieczenia "jednorazowej", gdzie wszystkie niezbędne poświadczenia zabezpieczeń są wysyłane w pojedynczym komunikacie, ustawiając `negotiateServiceCredential` atrybutu \<komunikatu > element konfiguracji do `false`.  
  
 Jednorazowej uwierzytelnianie nie działa z kontrakty dwukierunkowe.  
  
 Dla kontraktów "żądanie-odpowiedź" jednorazowej uwierzytelnianie działa tylko wtedy, gdy stos powiązania poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IRequestChannel> lub <xref:System.ServiceModel.Channels.IRequestSessionChannel> wystąpień.  
  
 Dla kontraktów jednokierunkowych jednorazowej uwierzytelniania działa, gdy stos powiązania poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, <xref:System.ServiceModel.Channels.IOutputChannel> lub <xref:System.ServiceModel.Channels.IOutputSessionChannel> wystąpień.  
  
### <a name="cookie-mode-security-context-tokens"></a>Tryb plików cookie zabezpieczeń kontekstu tokenów  
 Nie można używać tokenów kontekstu zabezpieczeń trybu plików cookie z kontrakty dwukierunkowe.  
  
 Dla kontraktów "żądanie-odpowiedź", kontekst zabezpieczeń trybu plików cookie tokenów pracy tylko wtedy, gdy stos powiązania poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IRequestChannel> lub <xref:System.ServiceModel.Channels.IRequestSessionChannel> wystąpień.  
  
 Dla kontraktów jednokierunkowych kontekstu zabezpieczeń trybu plików cookie tokenów działa, jeśli stosu powiązania poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IRequestChannel> lub <xref:System.ServiceModel.Channels.IRequestSessionChannel> wystąpień.  
  
### <a name="session-mode-security-context-tokens"></a>Tokeny kontekstu zabezpieczeń trybu sesji  
 Tryb sesji SCT działa w przypadku kontrakty dwukierunkowe Jeśli stosu powiązania poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IDuplexChannel> lub <xref:System.ServiceModel.Channels.IDuplexSessionChannel> wystąpień.  
  
 Tryb sesji SCT działa dla kontraktów "żądanie-odpowiedź", jeśli stosu powiązania poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> lub <xref:System.ServiceModel.Channels.IRequestSessionChannel>, wystąpień.  
  
 Tryb sesji SCT działa w przypadku umów sposób 1 Jeśli stosu powiązania poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> lub <xref:System.ServiceModel.Channels.IRequestSessionChannel> wystąpień.  
  
## <a name="deriving-from-a-standard-binding"></a>Wyprowadzanie z Powiązanie standardowe  
 Zamiast tworzenia nowej klasy powiązanie, może być możliwe zwiększenie jeden z istniejących powiązań dostarczanych przez system. Podobnie jak w poprzednim przypadku nr, konieczne jest przesłonięcie <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metody i <xref:System.ServiceModel.Channels.Binding.Scheme%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.Binding>
- [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)
