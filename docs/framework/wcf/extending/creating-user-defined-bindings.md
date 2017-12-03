---
title: "Tworzenie powiązań zdefiniowanych przez użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c54f5b25a4391b4758e1798bce6e03f4534332db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="creating-user-defined-bindings"></a>Tworzenie powiązań zdefiniowanych przez użytkownika
Istnieje kilka sposobów, aby utworzyć powiązania nie są dostarczane przez system:  
  
-   Tworzenie niestandardowego powiązania, na podstawie <xref:System.ServiceModel.Channels.CustomBinding> klasy, która jest kontenerem, który należy wypełnić elementy powiązania. Wiązanie niestandardowe jest dodawane do punktu końcowego usługi. Można utworzyć niestandardowego powiązania, które albo programowo lub w konfiguracji aplikacji pliku. Aby użyć elementu powiązania z pliku konfiguracji aplikacji, musi rozszerzać element powiązania <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]powiązania niestandardowe, zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md) i <xref:System.ServiceModel.Channels.CustomBinding>.  
  
-   Można utworzyć klasy, która pochodzi z Powiązanie standardowe. Na przykład mogą dziedziczyć klasy z <xref:System.ServiceModel.WSHttpBinding> i zastąpić <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> metodę, aby uzyskać elementy wiązania i Wstaw element niestandardowego powiązania lub ustanawiania konkretną wartość zabezpieczeń.  
  
-   Można utworzyć nowy <xref:System.ServiceModel.Channels.Binding> typu całkowicie kontrolować implementacji całego powiązania.  
  
## <a name="the-order-of-binding-elements"></a>Kolejność elementów wiązania  
 Każdy element powiązania reprezentuje krok przetwarzania przy wysyłaniu lub odbieraniu wiadomości. W czasie wykonywania elementy powiązania tworzenia kanałów i odbiorników niezbędne do utworzenia stosy kanału przychodzących i wychodzących.  
  
 Istnieją trzy typy elementy powiązania: elementy powiązania protokołu, kodowania elementów wiązania i elementy powiązania transportu.  
  
 Elementy powiązania protokołu — te elementy reprezentują wyższego poziomu przetwarzania czynności, które działają w wiadomości. Kanałów i odbiorników utworzone przez te elementy powiązania można dodać, usunąć lub zmodyfikować zawartość komunikatu. Podane powiązanie może mieć dowolną liczbę elementy powiązania protokołu, każdy dziedziczenie z <xref:System.ServiceModel.Channels.BindingElement>. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]zawiera kilka elementów powiązania protokołu, w tym <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> i <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
 Kodowanie elementu powiązania — te stanowią elementy przekształceń między komunikat i kodowania gotowe do transmisji w sieci. Typowy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania zawierać dokładnie jeden element powiązania kodowania. Kodowanie elementy powiązania przykłady <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>i <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Jeśli nie określono kodowanie elementu powiązania dla powiązania, domyślnym kodowaniem jest używany. Wartość domyślna to tekst w przypadku transportu HTTP i dane binarne w przeciwnym razie wartość.  
  
 Element powiązania transportu — te elementy reprezentują transmisji kodowania komunikatu protokołu transportu. Typowy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania zawierać dokładnie jeden element powiązania transportu, który dziedziczy <xref:System.ServiceModel.Channels.TransportBindingElement>. Przykłady transportu elementów wiązania <xref:System.ServiceModel.Channels.TcpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement>i <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>.  
  
 Podczas tworzenia nowego powiązania ważna jest kolejność elementów powiązania dodany. Zawsze dodawaj elementy powiązania w następującej kolejności:  
  
|Warstwy|Opcje|Wymagane|  
|-----------|-------------|--------------|  
|Przepływ transakcji|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Nie|  
|Niezawodność|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Nie|  
|Zabezpieczenia|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Nie|  
|Złożone dupleks|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Nie|  
|Kodowanie|Tekst, Binary, MTOM, niestandardowe|Tak*|  
|Transportu|TCP i nazwane potoki, HTTP, HTTPS, usługa MSMQ, niestandardowe|Tak|  
  
 * Ponieważ jest wymagane kodowanie dla każdego powiązania, jeśli nie określono kodowania, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dodaje domyślne kodowanie dla Ciebie. Wartość domyślna to Text/XML dla transportu HTTP i HTTPS, a danych binarnych w przeciwnym razie wartość.  
  
## <a name="creating-a-new-binding-element"></a>Tworzenie nowego elementu powiązania  
 Oprócz typów pochodnych <xref:System.ServiceModel.Channels.BindingElement> są dostarczane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], możesz utworzyć własne elementy powiązania. Dzięki temu można dostosować sposób stosu powiązania jest tworzony i składników, które Przejdź w niej, tworząc własne <xref:System.ServiceModel.Channels.BindingElement> mogą się składać z innych typów dostarczane przez system na stosie.  
  
 Na przykład w przypadku zastosowania `LoggingBindingElement` zapewnia możliwość rejestrowania komunikatu do bazy danych, należy go umieścić powyżej kanał transportu w stosie kanału. W takim przypadku aplikacja tworzy niestandardowego powiązania, które składa się `LoggingBindingElement` z `TcpTransportBindingElement`, jak w poniższym przykładzie.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 Jak zapisać nazwę nowego elementu powiązania zależy od jego działanie dokładnie. Jedną z próbek, [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md), zawiera szczegółowy opis sposobu wdrażania jednego rodzaju elementu powiązania.  
  
## <a name="creating-a-new-binding"></a>Tworzenie nowego powiązania  
 Element powiązania utworzonych przez użytkownika może służyć na dwa sposoby. Poprzedniej sekcji przedstawiono sposób pierwszy: za pomocą niestandardowego powiązania. Niestandardowe powiązanie umożliwia użytkownikom tworzenie własnych powiązania na podstawie dowolnego zestawu powiązania elementów, w tym te utworzone przez użytkownika.  
  
 Użycie powiązania w więcej niż jedną aplikację, Utwórz własne powiązania i rozszerzanie <xref:System.ServiceModel.Channels.Binding>. Dzięki temu można uniknąć ręcznego tworzenia niestandardowego powiązania za każdym razem, gdy chcesz jej używać. Powiązania zdefiniowane przez użytkownika umożliwia definiowanie zachowania wiązania i obejmują elementy wiązania zdefiniowane przez użytkownika. I jest *wstępnie opakowane*: nie masz odbudować powiązania w każdym razem podczas wykonywania.  
  
 Co najmniej powiązania zdefiniowane przez użytkownika musi implementować <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> — metoda i <xref:System.ServiceModel.Channels.Binding.Scheme%2A> właściwości.  
  
 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> Metoda zwraca nową <xref:System.ServiceModel.Channels.BindingElementCollection> zawierającą elementy wiązania dla wiązania. Kolekcja jest określona i powinna zawierać elementy powiązania protokołu najpierw, a następnie element powiązania kodowania, a następnie element powiązania transportu. Korzystając z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] elementy wiązania dostarczane przez system, należy wykonać element powiązania reguły określone w kolejności [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md). Ta kolekcja nigdy nie powinien odwoływać się w klasie powiązania zdefiniowane przez użytkownika; odwoływać się do obiektów w związku z tym, autorzy powiązania musi zwracać `Clone()` z <xref:System.ServiceModel.Channels.BindingElementCollection> na każde wywołanie <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>.  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> Właściwość reprezentuje schemat identyfikatora URI używany dla powiązania protokołu transportu. Na przykład *WSHttpBinding* i *NetTcpBinding* zwrócić "http" i "net.tcp" z odpowiednich <xref:System.ServiceModel.Channels.Binding.Scheme%2A> właściwości.  
  
 Aby uzyskać pełną listę możliwych metod i właściwości dla powiązań zdefiniowanych przez użytkownika, zobacz <xref:System.ServiceModel.Channels.Binding>.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie implementuje powiązanie profilu w `SampleProfileUdpBinding`, która jest pochodną <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` Zawiera maksymalnie cztery elementy powiązania w nim: jeden użytkownik utworzył `UdpTransportBindingElement`; i trzy dostarczane przez system: `TextMessageEncodingBindingElement`, `CompositeDuplexBindingElement`, i `ReliableSessionBindingElement`.  
  
```  
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
  
## <a name="security-restrictions-with-duplex-contracts"></a>Ograniczenia zabezpieczeń z kontrakty dwukierunkowe  
 Nie wszystkie elementy powiązania są niezgodne ze sobą. W szczególności istnieją pewne ograniczenia dotyczące zabezpieczeń elementy wiązania, gdy jest używany z kontraktów dupleksowych.  
  
### <a name="one-shot-security"></a>Jednorazowej zabezpieczeń  
 Można zaimplementować zabezpieczeń "jednorazowej", gdzie wszystkie niezbędne poświadczenia zabezpieczeń, jakim są wysyłane w pojedynczym komunikacie, ustawiając `negotiateServiceCredential` atrybutu \<wiadomości > element konfiguracji do `false`.  
  
 Uwierzytelnianie jednorazowej nie działa z kontraktów dupleksowych.  
  
 Dla kontraktów "żądanie-odpowiedź" jednorazowej uwierzytelnianie działa tylko wtedy, gdy stos powiązanie poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IRequestChannel> lub <xref:System.ServiceModel.Channels.IRequestSessionChannel> wystąpień.  
  
 Dla kontraktów jednokierunkowych jednorazowej uwierzytelniania działa, gdy stos powiązanie poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, <xref:System.ServiceModel.Channels.IOutputChannel> lub <xref:System.ServiceModel.Channels.IOutputSessionChannel> wystąpień.  
  
### <a name="cookie-mode-security-context-tokens"></a>Tokenów kontekstów zabezpieczeń tryb plików cookie  
 Nie można używać tokenów kontekstów zabezpieczeń plików cookie w trybie z kontraktów dupleksowych.  
  
 Dla kontraktów "żądanie-odpowiedź" Tryb plików cookie kontekstu zabezpieczeń tokeny pracy tylko wtedy, gdy stos powiązanie poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IRequestChannel> lub <xref:System.ServiceModel.Channels.IRequestSessionChannel> wystąpień.  
  
 Dla kontraktów jednokierunkowych kontekstu zabezpieczeń tryb plików cookie tokeny działa, jeśli stosu powiązanie poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IRequestChannel> lub <xref:System.ServiceModel.Channels.IRequestSessionChannel> wystąpień.  
  
### <a name="session-mode-security-context-tokens"></a>Tokenów kontekstów zabezpieczeń trybu sesji  
 Tryb sesji SCT działa w przypadku kontrakty dwukierunkowe Jeśli stosu powiązanie poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IDuplexChannel> lub <xref:System.ServiceModel.Channels.IDuplexSessionChannel> wystąpień.  
  
 Tryb sesji SCT działa dla kontraktów "żądanie-odpowiedź", jeśli stosu powiązanie poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> lub <xref:System.ServiceModel.Channels.IRequestSessionChannel>, wystąpień.  
  
 Tryb sesji SCT działa w przypadku umów sposób 1 Jeśli stosu powiązanie poniżej elementu powiązania zabezpieczeń obsługuje tworzenie <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> lub <xref:System.ServiceModel.Channels.IRequestSessionChannel> wystąpień.  
  
## <a name="deriving-from-a-standard-binding"></a>Wyprowadzanie z Powiązanie standardowe  
 Zamiast tworzenia nowej klasy powiązanie, może być możliwe zwiększenie jedno z istniejących powiązań dostarczane przez system. Podobnie jak w przypadku poprzedniego konieczne jest przesłonięcie <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> — metoda i <xref:System.ServiceModel.Channels.Binding.Scheme%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.Binding>  
 [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)
