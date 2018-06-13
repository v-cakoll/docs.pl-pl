---
title: Kontrakt pierwszy programowanie usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: e5dbaa7b-005f-4330-848d-58ac4f42f093
ms.openlocfilehash: 10129fcb40d86d1ca7e42bce68b072e9118bcc88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519496"
---
# <a name="contract-first-workflow-service-development"></a>Kontrakt pierwszy programowanie usługi przepływu pracy
Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], funkcji Windows Workflow Foundation (WF) lepszą integrację usług sieci web i przepływów pracy w formularzu tworzenia pierwszej kontraktu przepływu pracy. Narzędzie do projektowania przepływu pracy pierwszy kontraktu pozwala na projektowanie najpierw kontraktu w kodzie. Narzędzie następnie automatycznie generuje szablon czynności w przyborniku operacji w umowie. Ten temat zawiera omówienie sposobu działania i właściwości w usłudze przepływu pracy mapowania atrybuty kontraktu usługi. Na przykład krok po kroku, tworzenie usługi przepływu pracy pierwszy kontraktu, zobacz [porady: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
-   [Mapowanie przepływu atrybutów atrybuty kontraktu usługi](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#MappingAttributes)  
  
    -   [Atrybuty kontraktu usługi](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ServiceContract)  
  
    -   [Operacja kontraktu atrybutów](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#OperationContract)  
  
    -   [Atrybuty kontraktu komunikatu](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#MessageContract)  
  
    -   [Atrybuty kontraktu danych](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#DataContract)  
  
    -   [Atrybuty kontrakt błędu](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#FaultContract)  
  
-   [Dodatkowego pomocy technicznej i informacji o implementacji](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#AdditionalSupport)  
  
    -   [Funkcji kontraktu usługi nieobsługiwane](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
    -   [Generowanie skonfigurowanych działania obsługi wiadomości](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ActivityGeneration)  
  
##  <a name="MappingAttributes"></a> Mapowanie przepływu atrybutów atrybuty kontraktu usługi  
 Tabele w poniższych sekcjach określ różne WCF atrybuty, właściwości i jak są mapowane do obsługi komunikatów działań i właściwości w przepływie pracy pierwszy kontraktu.  
  
-   [Atrybuty kontraktu usługi](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ServiceContract)  
  
-   [Operacja kontraktu atrybutów](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#OperationContract)  
  
-   [Atrybuty kontraktu komunikatu](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#MessageContract)  
  
-   [Atrybuty kontraktu danych](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#DataContract)  
  
-   [Atrybuty kontrakt błędu](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#FaultContract)  
  
###  <a name="ServiceContract"></a> Atrybuty kontraktu usługi  
  
|Nazwa właściwości|Obsługiwane|Opis|Sprawdzanie poprawności WF|  
|-------------------|---------------|-----------------|-------------------|  
|CallbackContract|Nie|Pobiera lub ustawia typ kontraktu wywołania zwrotnego w przypadku kontraktu dupleksowego.|(NIE DOTYCZY)|  
|ConfigurationName|Nie|Pobiera lub ustawia nazwę używaną do lokalizowania usługi w pliku konfiguracyjnym aplikacji.|(NIE DOTYCZY)|  
|HasProtectionLevel|Tak|Pobiera wartość wskazującą, czy element członkowski ma przypisano poziomu ochrony.|Receive.ProtectionLevel nie może mieć wartości null.|  
|Nazwa|Tak|Pobiera lub ustawia nazwę \<portType > elementu w sieci Web Services Description Language (WSDL).|Receive.ServiceContractName.LocalName powinna być zgodna.|  
|Przestrzeń nazw|Tak|Pobiera lub ustawia obszar nazw \<portType > elementu w sieci Web Services Description Language (WSDL).|Receive.ServiceContractName.NameSpace powinna być zgodna.|  
|protectionLevel|Tak|Określa, czy powiązania dla kontraktu musi obsługiwać wartości właściwości ProtectionLevel.|Receive.ProtectionLevel powinna być zgodna.|  
|SessionMode|Nie|Pobiera lub ustawia, czy sesje są dozwolone, nie dozwolona lub wymagana.|(NIE DOTYCZY)|  
|TypeId|Nie|Po zaimplementowaniu w klasie pochodnej pobiera unikatowy identyfikator dla tego atrybutu. (Dziedziczone z atrybutu).|(NIE DOTYCZY)|  
  
 Tutaj wstaw treść podsekcji.  
  
###  <a name="OperationContract"></a> Operacja kontraktu atrybutów  
  
|Nazwa właściwości|Obsługiwane|Opis|Sprawdzanie poprawności WF|  
|-------------------|---------------|-----------------|-------------------|  
|Akcja|Tak|Pobiera lub ustawia akcję WS-Addressing komunikatu żądania.|Receive.Action powinna być zgodna.|  
|AsyncPattern|Nie|Wskazuje, że operacja jest zaimplementowana asynchronicznie za pomocą początkowy\<methodName > i End\<methodName > pary metod w kontrakcie usługi.|(NIE DOTYCZY)|  
|HasProtectionLevel|Tak|Pobiera wartość wskazującą, czy komunikaty dla tej operacji musi być zaszyfrowany, podpisany, lub obie.|Receive.ProtectionLevel nie może mieć wartości null.|  
|IsInitiating|Nie|Pobiera lub ustawia wartość wskazującą, czy metoda implementuje operację umożliwiającą inicjację sesji na serwerze (jeśli istnieje sesji programu).|(NIE DOTYCZY)|  
|Ustawienie właściwości IsOneWay|Tak|Pobiera lub ustawia wartość wskazującą, czy operacja zwraca komunikat odpowiedzi.|(Otrzymywać nie SendReply dla tej lub nie ReceiveReply dla tego Wyślij).|  
|IsTerminating|Nie|Pobiera lub ustawia wartość wskazującą, czy operacji usługi powoduje serwer Zamknij sesję po komunikat odpowiedzi, jeśli istnieje, jest wysyłane.|(NIE DOTYCZY)|  
|Nazwa|Tak|Pobiera lub ustawia nazwę operacji.|Receive.OperationName powinna być zgodna.|  
|protectionLevel|Tak|Pobiera lub ustawia wartość określającą, czy komunikaty operacji musi być zaszyfrowany, podpisany, lub obie.|Receive.ProtectionLevel powinna być zgodna.|  
|Parametr ReplyAction|Tak|Pobiera lub ustawia wartość akcji SOAP dla komunikatu odpowiedzi operacji.|SendReply.Action powinna być zgodna.|  
|TypeId|Nie|Po zaimplementowaniu w klasie pochodnej pobiera unikatowy identyfikator dla tego atrybutu. (Dziedziczone z atrybutu).|(NIE DOTYCZY)|  
  
###  <a name="MessageContract"></a> Atrybuty kontraktu komunikatu  
  
|Nazwa właściwości|Obsługiwane|Opis|Sprawdzanie poprawności WF|  
|-------------------|---------------|-----------------|-------------------|  
|HasProtectionLevel|Tak|Pobiera wartość wskazującą, czy wiadomość ma poziom ochrony.|Nie sprawdzania poprawności (Receive.Content i SendReply.Content muszą być zgodne typ kontraktu komunikatu).|  
|Atrybut IsWrapped|Tak|Pobiera lub ustawia wartość określającą, czy treść komunikatu ma element otoki.|Nie sprawdzania poprawności (Receive.Content i Sendreply.Content muszą być zgodne typ kontraktu komunikatu).|  
|protectionLevel|Nie|Pobiera lub ustawia wartość, która określić, czy wiadomości muszą być szyfrowane, podpisany, lub obie.|(NIE DOTYCZY)|  
|TypeId|Tak|Po zaimplementowaniu w klasie pochodnej pobiera unikatowy identyfikator dla tego atrybutu. (Dziedziczone z atrybutu).|Nie sprawdzania poprawności (Receive.Content i SendReply.Content muszą być zgodne typ kontraktu komunikatu).|  
|WrapperName|Tak|Pobiera lub ustawia nazwę elementu otoki treści wiadomości.|Nie sprawdzania poprawności (Receive.Content i SendReply.Content muszą być zgodne typ kontraktu komunikatu).|  
|WrapperNamespace|Nie|Pobiera lub ustawia obszar nazw elementu otoki treści wiadomości.|(NIE DOTYCZY)|  
  
###  <a name="DataContract"></a> Atrybuty kontraktu danych  
  
|Nazwa właściwości|Obsługiwane|Opis|Sprawdzanie poprawności WF|  
|-------------------|---------------|-----------------|-------------------|  
|IsReference|Nie|Pobiera lub ustawia wartość wskazującą, czy chcesz zachować dane odwołanie do obiektu.|(NIE DOTYCZY)|  
|Nazwa|Tak|Pobiera lub ustawia nazwę kontraktu danych dla typu.|Nie sprawdzania poprawności (Receive.Content i SendReply.Content muszą być zgodne typ kontraktu komunikatu).|  
|Przestrzeń nazw|Tak|Pobiera lub ustawia przestrzeń nazw kontraktu danych dla typu.|Nie sprawdzania poprawności (Receive.Content i SendReply.Content muszą być zgodne typ kontraktu komunikatu).|  
|TypeId|Nie|Po zaimplementowaniu w klasie pochodnej pobiera unikatowy identyfikator dla tego atrybutu. (Dziedziczone z atrybutu).|(NIE DOTYCZY)|  
  
###  <a name="FaultContract"></a> Atrybuty kontrakt błędu  
  
|Nazwa właściwości|Obsługiwane|Opis|Sprawdzanie poprawności WF|  
|-------------------|---------------|-----------------|-------------------|  
|Akcja|Tak|Pobiera lub ustawia akcję komunikat o błędzie SOAP, który jest określony jako część kontrakt operacji.|SendReply.Action powinna być zgodna.|  
|DetailType|Tak|Pobiera typ możliwy do serializacji obiektu, który zawiera informacje o błędzie.|SendReply.Content powinien być zgodny z typem|  
|HasProtectionLevel|Nie|Pobiera wartość wskazującą, czy komunikat o błędzie protokołu SOAP ma przypisano poziomu ochrony.|(NIE DOTYCZY)|  
|Nazwa|Nie|Pobiera lub ustawia nazwę komunikat o błędzie w sieci Web Services Description Language (WSDL).|(NIE DOTYCZY)|  
|Przestrzeń nazw|Nie|Pobiera lub ustawia obszar nazw błędu protokołu SOAP.|(NIE DOTYCZY)|  
|protectionLevel|Nie|Określa poziom ochrony wymaga błędu protokołu SOAP z powiązania.|(NIE DOTYCZY)|  
|TypeId|Nie|Po zaimplementowaniu w klasie pochodnej pobiera unikatowy identyfikator dla tego atrybutu. (Dziedziczone z atrybutu).|(NIE DOTYCZY)|  
  
##  <a name="AdditionalSupport"></a> Dodatkowego pomocy technicznej i informacji o implementacji  
  
-   [Funkcji kontraktu usługi nieobsługiwane](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
-   [Generowanie skonfigurowanych działania obsługi wiadomości](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ActivityGeneration)  
  
###  <a name="UnsupportedFeatures"></a> Funkcji kontraktu usługi nieobsługiwane  
  
-   Używanie zadań w TPL (Biblioteka zadań równoległych) w kontraktach nie jest obsługiwane.  
  
-   Dziedziczenie w kontraktach usług nie jest obsługiwane.  
  
###  <a name="ActivityGeneration"></a> Generowanie skonfigurowanych działania obsługi wiadomości  
 Dwie metody statyczne publiczne są dodawane do <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań do wspierania tworzenia wstępnie skonfigurowanych działania komunikat podczas korzystania z usług przepływu pracy pierwszy kontraktu.  
  
-   <xref:System.ServiceModel.Activities.Receive.FromOperationDescription%2A?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Activities.SendReply.FromOperationDescription%2A?displayProperty=nameWithType>  
  
 Działanie generowane przy użyciu tej metody należy przeszedł pomyślnie weryfikacji kontraktu i w związku z tym te metody są używane wewnętrznie jako część logiki sprawdzania poprawności dla <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>. <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>, <xref:System.ServiceModel.Activities.Receive.Action%2A>, <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>, <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A>, I <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> są wszystkie wstępnie skonfigurowane do dopasowania importowanych kontraktu. Na stronie właściwości zawartości dla działań w Projektancie przepływów pracy **komunikat** lub **parametry** sekcje są również wstępnie skonfigurowane, aby dopasować kontraktu.  
  
 Skonfigurowane błędów WCF kontrakty również są obsługiwane przez zwrócenie osobny zestaw <xref:System.ServiceModel.Activities.SendReply> działań dla każdego z usterek, które są widoczne w <xref:System.ServiceModel.Description.OperationDescription.Faults%2A> <xref:System.ServiceModel.Description.FaultDescriptionCollection>.  
  
 Dla innych części <xref:System.ServiceModel.Description.OperationDescription> które są obsługiwane przez usługi WF dzisiaj (np. zachowania WebGet/WebInvoke lub zachowania operacja niestandardowa), interfejsu API będzie ignorować te wartości jako część generowania i konfiguracji. Żadne wyjątki nie będą zgłaszane.
