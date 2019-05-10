---
title: Programowanie usługi przepływu pracy narzędzia Contract-First
ms.date: 03/30/2017
ms.assetid: e5dbaa7b-005f-4330-848d-58ac4f42f093
ms.openlocfilehash: 2fcc0054a3e4c9dd2152344617c8506c9ce6b0d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587607"
---
# <a name="contract-first-workflow-service-development"></a>Programowanie usługi przepływu pracy narzędzia Contract-First
Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], funkcji Windows Workflow Foundation (WF) lepszą integrację między usługami sieci web i przepływów pracy w formie Projektowanie przepływów pracy z wymogiem wcześniejszego zawarcia kontraktu. Narzędzie tworzenia przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu umożliwia projektowanie najpierw kontrakt w kodzie. Narzędzie następnie automatycznie generuje szablon działania w przyborniku dla operacji w kontrakcie. Ten temat zawiera omówienie sposobu działania i właściwości w usłudze przepływu pracy mapowania na atrybuty kontraktu usługi. Aby uzyskać przykład krok po kroku tworzenia przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu usługi, zobacz [jak: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
- [Mapowanie atrybutów kontraktu usługi do atrybutów przepływu pracy](contract-first-workflow-service-development.md#MappingAttributes)  
  
    - [Atrybuty kontraktu usługi](contract-first-workflow-service-development.md#ServiceContract)  
  
    - [Atrybuty kontrakt operacji](contract-first-workflow-service-development.md#OperationContract)  
  
    - [Atrybuty kontraktu komunikatu](contract-first-workflow-service-development.md#MessageContract)  
  
    - [Atrybuty kontraktu danych](contract-first-workflow-service-development.md#DataContract)  
  
    - [Atrybuty kontraktu błędów](contract-first-workflow-service-development.md#FaultContract)  
  
- [Dodatkowa pomoc techniczna i informacje o implementacji](contract-first-workflow-service-development.md#AdditionalSupport)  
  
    - [Nieobsługiwane funkcje kontraktu](contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
    - [Generowanie skonfigurowanych działań dotyczących komunikatów](contract-first-workflow-service-development.md#ActivityGeneration)  
  
## <a name="MappingAttributes"></a> Mapowanie atrybutów kontraktu usługi do atrybutów przepływu pracy  
 Tabele w poniższych sekcjach określ różne WCF atrybutów, właściwości i jak są mapowane do obsługi komunikatów działań i właściwości w przepływie pracy z wymogiem wcześniejszego zawarcia kontraktu.  
  
- [Atrybuty kontraktu usługi](contract-first-workflow-service-development.md#ServiceContract)  
  
- [Atrybuty kontrakt operacji](contract-first-workflow-service-development.md#OperationContract)  
  
- [Atrybuty kontraktu komunikatu](contract-first-workflow-service-development.md#MessageContract)  
  
- [Atrybuty kontraktu danych](contract-first-workflow-service-development.md#DataContract)  
  
- [Atrybuty kontraktu błędów](contract-first-workflow-service-development.md#FaultContract)  
  
### <a name="ServiceContract"></a> Atrybuty kontraktu usługi  
  
|Nazwa właściwości|Obsługiwane|Opis|Sprawdzanie poprawności WF|  
|-------------------|---------------|-----------------|-------------------|  
|CallbackContract|Nie|Pobiera lub ustawia typ kontrakt wywołania zwrotnego, gdy kontrakt jest kontraktu dwukierunkowego.|(N/D)|  
|ConfigurationName|Nie|Pobiera lub ustawia nazwę używaną do lokalizowania usługi w pliku konfiguracji aplikacji.|(N/D)|  
|HasProtectionLevel|Yes|Pobiera wartość wskazującą, czy element członkowski ma przypisany poziom ochrony.|Receive.ProtectionLevel nie może mieć wartości null.|  
|Nazwa|Yes|Pobiera lub ustawia nazwę \<portType > elementu w sieci Web Services Description Language (WSDL).|Receive.ServiceContractName.LocalName powinny być zgodne.|  
|Przestrzeń nazw|Yes|Pobiera lub ustawia obszar nazw \<portType > elementu w sieci Web Services Description Language (WSDL).|Receive.ServiceContractName.NameSpace powinny być zgodne.|  
|protectionLevel|Yes|Określa, czy powiązania dla kontraktu musi obsługiwać wartość właściwości ProtectionLevel.|Receive.ProtectionLevel powinny być zgodne.|  
|SessionMode|Nie|Pobiera lub ustawia informację, czy sesje są dozwolone, niedozwolone lub wymagane.|(N/D)|  
|TypeId|Nie|Po zaimplementowaniu w klasie pochodnej pobiera unikatowy identyfikator dla tego atrybutu. (Dziedziczone z atrybutu).|(N/D)|  
  
 Tutaj wstaw treść podsekcji.  
  
### <a name="OperationContract"></a> Atrybuty kontrakt operacji  
  
|Nazwa właściwości|Obsługiwane|Opis|Sprawdzanie poprawności WF|  
|-------------------|---------------|-----------------|-------------------|  
|Akcja|Tak|Pobiera lub ustawia akcję WS-Addressing komunikatu żądania.|Receive.Action powinny być zgodne.|  
|AsyncPattern|Nie|Wskazuje, czy operacja jest zaimplementowana asynchronicznie za pomocą początkowy\<methodName > i na końcu\<methodName > pary metod w kontrakcie usługi.|(N/D)|  
|HasProtectionLevel|Tak|Pobiera wartość wskazującą, czy komunikaty dla tej operacji musi być szyfrowana, podpisany, lub obu.|Receive.ProtectionLevel nie może mieć wartości null.|  
|IsInitiating|Nie|Pobiera lub ustawia wartość wskazującą, czy metoda implementuje operację, która może zainicjować sesji na serwerze (jeśli takie sesji istnieje).|(N/D)|  
|IsOneWay|Tak|Pobiera lub ustawia wartość wskazującą, czy operacja zwraca komunikat odpowiedzi.|(Nie SendReply tego odbierania lub nie ReceiveReply dla tego Wyślij).|  
|IsTerminating|Nie|Pobiera lub ustawia wartość wskazującą, czy operacja usługi powoduje serwer Zamknij sesję po komunikat odpowiedzi, jeśli istnieje, zostanie wysłany.|(N/D)|  
|Nazwa|Tak|Pobiera lub ustawia nazwę operacji.|Receive.OperationName powinny być zgodne.|  
|protectionLevel|Tak|Pobiera lub ustawia wartość określającą, czy komunikaty operacji musi być szyfrowana, podpisany, lub obu.|Receive.ProtectionLevel powinny być zgodne.|  
|Parametr ReplyAction|Tak|Pobiera lub ustawia wartość Akcja SOAP komunikat odpowiedzi operacji.|SendReply.Action powinny być zgodne.|  
|TypeId|Nie|Po zaimplementowaniu w klasie pochodnej pobiera unikatowy identyfikator dla tego atrybutu. (Dziedziczone z atrybutu).|(N/D)|  
  
### <a name="MessageContract"></a> Atrybuty kontraktu komunikatu  
  
|Nazwa właściwości|Obsługiwane|Opis|Sprawdzanie poprawności WF|  
|-------------------|---------------|-----------------|-------------------|  
|HasProtectionLevel|Tak|Pobiera wartość wskazującą, czy wiadomość zawiera poziom ochrony.|Nie nastąpi sprawdzanie poprawności (Receive.Content i SendReply.Content muszą być zgodne typ kontraktu komunikatu).|  
|Atrybut IsWrapped|Tak|Pobiera lub ustawia wartość określającą, czy treść komunikatu ma element otoki.|Nie nastąpi sprawdzanie poprawności (Receive.Content i Sendreply.Content muszą być zgodne typ kontraktu komunikatu).|  
|protectionLevel|Nie|Pobiera lub ustawia wartość, która jest określona, czy wiadomości musi być szyfrowana, podpisany, lub obu.|(N/D)|  
|TypeId|Yes|Po zaimplementowaniu w klasie pochodnej pobiera unikatowy identyfikator dla tego atrybutu. (Dziedziczone z atrybutu).|Nie nastąpi sprawdzanie poprawności (Receive.Content i SendReply.Content muszą być zgodne typ kontraktu komunikatu).|  
|WrapperName|Yes|Pobiera lub ustawia nazwę elementu otoki treści wiadomości.|Nie nastąpi sprawdzanie poprawności (Receive.Content i SendReply.Content muszą być zgodne typ kontraktu komunikatu).|  
|WrapperNamespace|Nie|Pobiera lub ustawia obszar nazw elementu otoki treści komunikatu.|(N/D)|  
  
### <a name="DataContract"></a> Atrybuty kontraktu danych  
  
|Nazwa właściwości|Obsługiwane|Opis|Sprawdzanie poprawności WF|  
|-------------------|---------------|-----------------|-------------------|  
|isReference|Nie|Pobiera lub ustawia wartość wskazującą, czy chcesz zachować dane odwołanie do obiektu.|(N/D)|  
|Nazwa|Tak|Pobiera lub ustawia nazwę kontraktu danych dla typu.|Nie nastąpi sprawdzanie poprawności (Receive.Content i SendReply.Content muszą być zgodne typ kontraktu komunikatu).|  
|Przestrzeń nazw|Yes|Pobiera lub ustawia obszar nazw dla kontraktu danych dla typu.|Nie nastąpi sprawdzanie poprawności (Receive.Content i SendReply.Content muszą być zgodne typ kontraktu komunikatu).|  
|TypeId|Nie|Po zaimplementowaniu w klasie pochodnej pobiera unikatowy identyfikator dla tego atrybutu. (Dziedziczone z atrybutu).|(N/D)|  
  
### <a name="FaultContract"></a> Atrybuty kontraktu błędów  
  
|Nazwa właściwości|Obsługiwane|Opis|Sprawdzanie poprawności WF|  
|-------------------|---------------|-----------------|-------------------|  
|Akcja|Tak|Pobiera lub ustawia akcję komunikat o błędzie protokołu SOAP, który jest określony jako część kontrakt operacji.|SendReply.Action powinny być zgodne.|  
|DetailType|Tak|Pobiera typ obiektu podlegającego serializacji, który zawiera informacje o błędzie.|SendReply.Content powinien być zgodny z typem|  
|HasProtectionLevel|Nie|Pobiera wartość wskazującą, czy komunikat o błędzie protokołu SOAP ma przypisany poziom ochrony.|(N/D)|  
|Nazwa|Nie|Pobiera lub ustawia nazwę komunikat o błędzie w sieci Web Services Description Language (WSDL).|(N/D)|  
|Przestrzeń nazw|Nie|Pobiera lub ustawia obszar nazw błąd protokołu SOAP.|(N/D)|  
|protectionLevel|Nie|Określa poziom ochrony, wymaganych przez błąd protokołu SOAP z wiązania.|(N/D)|  
|TypeId|Nie|Po zaimplementowaniu w klasie pochodnej pobiera unikatowy identyfikator dla tego atrybutu. (Dziedziczone z atrybutu).|(N/D)|  
  
## <a name="AdditionalSupport"></a> Dodatkowa pomoc techniczna i informacje o implementacji  
  
- [Nieobsługiwane funkcje kontraktu](contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
- [Generowanie skonfigurowanych działań dotyczących komunikatów](contract-first-workflow-service-development.md#ActivityGeneration)  
  
### <a name="UnsupportedFeatures"></a> Nieobsługiwane funkcje kontraktu  
  
- Użycie zadań TPL (Biblioteka zadań równoległych) w kontraktach nie jest obsługiwane.  
  
- Dziedziczenie w kontraktach usługi nie jest obsługiwane.  
  
### <a name="ActivityGeneration"></a> Generowanie skonfigurowanych działań dotyczących komunikatów  
 Dwie metody statyczne publiczne są dodawane do <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działania zmierzające do wspierania tworzenia wstępnie skonfigurowanej wiadomości działania podczas korzystania z usług przepływu pracy z wymogiem wcześniejszego zawarcia kontraktu.  
  
- <xref:System.ServiceModel.Activities.Receive.FromOperationDescription%2A?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Activities.SendReply.FromOperationDescription%2A?displayProperty=nameWithType>  
  
 Działanie generowanych przez te metody powinno być udanych weryfikacji kontraktu i w związku z tym te metody są używane wewnętrznie jako część logikę weryfikacji <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>. <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>, <xref:System.ServiceModel.Activities.Receive.Action%2A>, <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>, <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A>, I <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> są wszystkie wstępnie skonfigurowane, aby dopasować importowanych kontraktu. Na stronie właściwości zawartości dla działania w Projektancie przepływu pracy **komunikat** lub **parametry** sekcje są również wstępnie skonfigurowane, aby dopasować umowy.  
  
 Skonfigurowane błędów programu WCF kontraktów również są obsługiwane przez zwrócenie oddzielny zestaw <xref:System.ServiceModel.Activities.SendReply> działania dla wszystkich błędów, które pojawiają się w <xref:System.ServiceModel.Description.OperationDescription.Faults%2A> <xref:System.ServiceModel.Description.FaultDescriptionCollection>.  
  
 W innych częściach <xref:System.ServiceModel.Description.OperationDescription> , nie są obsługiwane przez usługi WF już dziś (np. WebGet/WebInvoke zachowania lub zachowań niestandardowych operacji), interfejs API będzie ignorować te wartości jako część generowania i konfiguracji. Zostanie zgłoszony, bez wyjątków.
