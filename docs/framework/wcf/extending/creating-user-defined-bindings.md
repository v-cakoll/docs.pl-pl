---
title: Tworzenie wiązań zdefiniowanych przez użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 34100569dc5cd5a340abca66fedca40ba21c1e0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185641"
---
# <a name="creating-user-defined-bindings"></a>Tworzenie wiązań zdefiniowanych przez użytkownika
Istnieje kilka sposobów tworzenia powiązań nie dostarczonych przez system:  
  
- Utwórz niestandardowe powiązanie, na podstawie <xref:System.ServiceModel.Channels.CustomBinding> klasy, która jest kontenerem, który wypełniasz elementami wiązania. Niestandardowe powiązanie jest następnie dodawane do punktu końcowego usługi. Powiązanie niestandardowe można utworzyć programowo lub w pliku konfiguracji aplikacji. Aby użyć elementu wiązania z pliku konfiguracji aplikacji, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>element wiązania musi zostać rozszerzony . Aby uzyskać więcej informacji na temat powiązań niestandardowych, zobacz [Powiązania niestandardowe](custom-bindings.md) i <xref:System.ServiceModel.Channels.CustomBinding>.  
  
- Można utworzyć klasę, która pochodzi od standardowego powiązania. Na przykład można wyprowadzić klasę <xref:System.ServiceModel.WSHttpBinding> z i <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> zastąpić metodę, aby uzyskać elementy wiązania i wstawić niestandardowy element wiązania lub ustanowić określoną wartość zabezpieczeń.  
  
- Można utworzyć nowy <xref:System.ServiceModel.Channels.Binding> typ, aby całkowicie kontrolować całą implementację powiązania.  
  
## <a name="the-order-of-binding-elements"></a>Kolejność elementów wiążących  
 Każdy element wiązania reprezentuje etap przetwarzania podczas wysyłania lub odbierania wiadomości. W czasie wykonywania elementy wiązania utworzyć kanały i odbiorniki niezbędne do tworzenia stosów kanałów wychodzących i przychodzących.  
  
 Istnieją trzy główne typy elementów wiązania: elementy wiązania protokołu, kodowanie elementów wiązania i elementy wiązania transportu.  
  
 Elementy wiązania protokołu — te elementy reprezentują kroki przetwarzania wyższego poziomu, które działają na komunikaty. Kanały i detektory utworzone przez te elementy wiązania można dodawać, usuwać lub modyfikować zawartość wiadomości. Dane powiązanie może mieć dowolną liczbę elementów wiązania <xref:System.ServiceModel.Channels.BindingElement>protokołu, z których każdy dziedziczy. Windows Communication Foundation (WCF) zawiera kilka <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> elementów <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>wiązania protokołu, w tym i .  
  
 Kodowanie elementu wiązania — te elementy reprezentują przekształcenia między wiadomością a kodowaniem gotowym do transmisji w sieci. Typowe powiązania WCF zawierają dokładnie jeden element wiązania kodowania. Przykłady elementów wiązania kodowania obejmują <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, , <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>i . <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> Jeśli element powiązania kodowania nie jest określony dla powiązania, używane jest kodowanie domyślne. Wartość domyślna to tekst, gdy transport jest HTTP i binarny w przeciwnym razie.  
  
 Element wiązania transportu — te elementy reprezentują transmisję komunikatu kodowania w protokole transportu. Typowe powiązania WCF obejmują dokładnie jeden element wiązania <xref:System.ServiceModel.Channels.TransportBindingElement>transportu, który dziedziczy po . Przykłady elementów wiązania <xref:System.ServiceModel.Channels.TcpTransportBindingElement>transportu <xref:System.ServiceModel.Channels.HttpTransportBindingElement>obejmują , <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>, i .  
  
 Podczas tworzenia nowych powiązań, kolejność dodanych elementów wiązania jest ważne. Zawsze dodawaj elementy wiązania w następującej kolejności:  
  
|Warstwa|Opcje|Wymagany|  
|-----------|-------------|--------------|  
|Przepływ transakcji|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Nie|  
|Niezawodność|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Nie|  
|Zabezpieczenia|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Nie|  
|Dwupoziomowy kompozyt|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Nie|  
|Kodowanie|Tekst, Binarny, MTOM, Niestandardowy|Tak\*|  
|Transport|TCP, nazwane potoki, HTTP, HTTPS, MSMQ, Niestandardowe|Tak|  
  
\*Ponieważ kodowanie jest wymagane dla każdego powiązania, jeśli kodowanie nie jest określony, WCF dodaje domyślne kodowanie dla Ciebie. Wartość domyślna to Tekst/XML dla transportów HTTP i HTTPS oraz Binarne w przeciwnym razie.  
  
## <a name="creating-a-new-binding-element"></a>Tworzenie nowego elementu wiązania  
 Oprócz typów pochodzących z <xref:System.ServiceModel.Channels.BindingElement> tych są dostarczane przez WCF, można utworzyć własne elementy wiązania. Dzięki temu można dostosować sposób stosu powiązań jest tworzony i składników, które <xref:System.ServiceModel.Channels.BindingElement> go w nim przez utworzenie własnego, który może być skomponowany z innymi typami dostarczonymi przez system w stosie.  
  
 Na przykład jeśli `LoggingBindingElement` zaimplementujesz, który zapewnia możliwość rejestrowania wiadomości do bazy danych, należy umieścić go nad kanałem transportu w stosie kanału. W takim przypadku aplikacja tworzy niestandardowe `LoggingBindingElement` powiązanie, które składa się z `TcpTransportBindingElement`, jak w poniższym przykładzie.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),
  new TcpTransportBindingElement()  
);  
```  
  
 Sposób pisania nowego elementu wiązania zależy od jego dokładnej funkcjonalności. Jeden z przykładów, [Transport: UDP](../samples/transport-udp.md), zawiera szczegółowy opis sposobu implementacji jednego rodzaju elementu wiązania.  
  
## <a name="creating-a-new-binding"></a>Tworzenie nowego powiązania  
 Utworzony przez użytkownika element wiązania może służyć na dwa sposoby. Poprzednia sekcja ilustruje pierwszy sposób: za pośrednictwem niestandardowego powiązania. Powiązanie niestandardowe umożliwia użytkownikowi tworzenie własnego powiązania na podstawie dowolnego zestawu elementów wiązania, w tym utworzonych przez użytkownika.  
  
 Jeśli używasz powiązania w więcej niż jednej aplikacji, <xref:System.ServiceModel.Channels.Binding>utwórz własne powiązanie i rozszerz plik . Pozwala to uniknąć ręcznego tworzenia niestandardowego powiązania za każdym razem, gdy chcesz go używać. Powiązanie zdefiniowane przez użytkownika umożliwia zdefiniowanie zachowania powiązania i dołączenie elementów wiązania zdefiniowanych przez użytkownika. I jest *wstępnie zapakowany:* nie trzeba odbudować wiązania za każdym razem, gdy go używasz.  
  
 Co najmniej powiązanie zdefiniowane przez <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> użytkownika musi <xref:System.ServiceModel.Channels.Binding.Scheme%2A> implementować metodę i właściwość.  
  
 Metoda <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> zwraca nowy, <xref:System.ServiceModel.Channels.BindingElementCollection> który zawiera elementy wiązania dla powiązania. Kolekcja jest uporządkowana i powinna zawierać elementy wiązania protokołu, po którym następuje element wiązania kodowania, a następnie element wiązania transportu. Korzystając z elementów wiązania dostarczonych przez system WCF, należy przestrzegać reguł zamawiania elementu wiązania określonego w [niestandardowych powiązaniach.](custom-bindings.md) Ta kolekcja nigdy nie powinna odwoływać się do obiektów, do których odwołuje się klasa wiązania zdefiniowana przez użytkownika; w związku z tym, `Clone()` wiążąci autorzy muszą zwrócić a <xref:System.ServiceModel.Channels.BindingElementCollection> każdego wezwania do <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>.  
  
 Właściwość <xref:System.ServiceModel.Channels.Binding.Scheme%2A> reprezentuje schemat URI dla protokołu transportu w użyciu na powiązanie. Na przykład *WSHttpBinding* i *NetTcpBinding* zwracają "http" i "net.tcp" z ich odpowiednich <xref:System.ServiceModel.Channels.Binding.Scheme%2A> właściwości.  
  
 Aby uzyskać pełną listę opcjonalnych metod i właściwości powiązań zdefiniowanych przez użytkownika, zobacz <xref:System.ServiceModel.Channels.Binding>.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie `SampleProfileUdpBinding`implementuje powiązanie <xref:System.ServiceModel.Channels.Binding>profilu w , który pochodzi od . Zawiera `SampleProfileUdpBinding` do czterech elementów wiązania w nim: jeden utworzony przez `UdpTransportBindingElement`użytkownika; i trzy dostarczane `TextMessageEncodingBindingElement`przez `CompositeDuplexBindingElement`system: , i `ReliableSessionBindingElement`.  
  
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
  
## <a name="security-restrictions-with-duplex-contracts"></a>Ograniczenia zabezpieczeń z kontraktami dupleksowymi  
 Nie wszystkie elementy wiązania są ze sobą kompatybilne. W szczególności istnieją pewne ograniczenia dotyczące elementów wiązania zabezpieczeń, gdy są używane z kontraktami dupleksowymi.  
  
### <a name="one-shot-security"></a>Bezpieczeństwo jednym strzałem  
 Można zaimplementować zabezpieczenia "one-shot", gdzie wszystkie niezbędne poświadczenia zabezpieczeń są `negotiateServiceCredential` wysyłane w \<jednej wiadomości, ustawiając atrybut komunikatu> element konfiguracji na `false`.  
  
 Uwierzytelnianie jednym strzałem nie działa z kontraktami dupleksowymi.  
  
 W przypadku kontraktów request-reply uwierzytelnianie jednokrotne działa tylko wtedy, <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel> gdy stos wiązania poniżej elementu wiązania zabezpieczeń obsługuje tworzenie lub wystąpienia.  
  
 W przypadku kontraktów jednokierunkowych uwierzytelnianie jednokrotne działa, jeśli <xref:System.ServiceModel.Channels.IRequestChannel>stos <xref:System.ServiceModel.Channels.IRequestSessionChannel> <xref:System.ServiceModel.Channels.IOutputChannel> wiązania <xref:System.ServiceModel.Channels.IOutputSessionChannel> poniżej elementu wiązania zabezpieczeń obsługuje tworzenie lub wystąpienia.  
  
### <a name="cookie-mode-security-context-tokens"></a>Tokeny kontekstu zabezpieczeń w trybie cookie  
 Tokeny kontekstu zabezpieczeń trybu plików cookie nie mogą być używane z kontraktami dupleksowymi.  
  
 W przypadku kontraktów request-reply tokeny kontekstu w trybie cookie działają tylko <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel> wtedy, gdy stos powiązania poniżej elementu wiązania zabezpieczeń obsługuje tworzenie lub wystąpienia.  
  
 W przypadku kontraktów jednokierunkowych tokeny kontekstu zabezpieczeń w trybie cookie <xref:System.ServiceModel.Channels.IRequestChannel> działają, jeśli stos powiązań poniżej elementu wiązania zabezpieczeń obsługuje tworzenie lub <xref:System.ServiceModel.Channels.IRequestSessionChannel> wystąpienia.  
  
### <a name="session-mode-security-context-tokens"></a>Tokeny kontekstu zabezpieczeń w trybie sesji  
 Tryb sesji SCT działa dla kontraktów dupleksu, jeśli <xref:System.ServiceModel.Channels.IDuplexChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel> stos wiązania poniżej elementu wiązania zabezpieczeń obsługuje tworzenie lub wystąpienia.  
  
 Tryb sesji SCT działa dla kontraktów request-reply, jeśli stos <xref:System.ServiceModel.Channels.IDuplexChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel>wiązania <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel>poniżej elementu wiązania zabezpieczeń obsługuje tworzenie , lub , wystąpień.  
  
 Tryb sesji SCT działa dla kontraktów jednokierunkowych, jeśli stos <xref:System.ServiceModel.Channels.IDuplexChannel>wiązania <xref:System.ServiceModel.Channels.IDuplexSessionChannel> <xref:System.ServiceModel.Channels.IRequestChannel> poniżej elementu wiązania zabezpieczeń obsługuje tworzenie , lub <xref:System.ServiceModel.Channels.IRequestSessionChannel> wystąpień.  
  
## <a name="deriving-from-a-standard-binding"></a>Wyprowadzenie ze standardowego powiązania  
 Zamiast tworzenia całkowicie nowej klasy wiązania, może być możliwe rozszerzenie jednego z istniejących powiązań dostarczonych przez system. Podobnie jak w poprzednim przypadku, należy <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> zastąpić metodę <xref:System.ServiceModel.Channels.Binding.Scheme%2A> i właściwość.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Channels.Binding>
- [Powiązania niestandardowe](custom-bindings.md)
