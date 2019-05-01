---
title: Lista działań
ms.date: 03/30/2017
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
ms.openlocfilehash: f96aab037e86b05096df7ffc82a0be3f6cce1ad2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998039"
---
# <a name="activity-list"></a>Lista działań
Ten temat zawiera listę wszystkich działań, które są zdefiniowane przez Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Działania można również zdefiniować programowo, aby śledzenie użytkowników grupy. Aby uzyskać więcej informacji, zobacz [emitowanie danych śledzenia User-Code](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
## <a name="servicemodel-activities"></a>Działania elementu ServiceModel  
 W poniższej tabeli wymieniono wszystkie działania dla scenariuszy użycia głównych.  
  
|Etykieta|Nazwa działania|Typ działania|Opis|  
|-----------|-------------------|-------------------|-----------------|  
|A, M|Działanie otoczenia|N/d (to nie są kontrolowane przez ServiceModel)|Działanie, którego identyfikator jest ustawione w protokole TLS przed wszelkie wywołania do kodu modelu ServiceModel (po stronie klienta lub po stronie serwera).<br /><br /> Przykład: Gdzie open nosi nazwę klienta WCF lub serviceHost.open działanie zostanie wywołane.|  
|B|Konstrukcja<br /><br /> Obiekt ChannelFactory. ContractType: "[Type]".|Konstrukcja||  
|C|Otwarcie<br /><br /> [ClientBase&#124;ChannelFactory]. ContractType: "[Type]".|Otwarcie||  
|I|Close [ClientBase&#124;ChannelFactory]. ContractType: "[Type]".|Zamknięcie||  
|M|Construct ServiceHost. Typ ServiceType: "[Type]".|Konstrukcja||  
|N|Open ServiceHost. Typ ServiceType: "[Type]".|Otwarcie||  
|Z|Zamknij ServiceHost. Typ ServiceType: "[Type]".|Zamknięcie||  
|O|Posłuchaj, w [address].|ListenAt|To i następnego działania są specyficzne dla transportu. Działania ListenAt reprezentuje zawartość, który jest mapowany do adresu, na którym nasłuchuje odbiornik kanału w. W przypadku usługi MSMQ jest on samej kolejki, ponieważ kolejka jest mapowany na jeden adres. To działanie nasłuchuje połączeń przychodzących w przypadku transportu nawiązaniem połączenia, dla wiadomości usługi MSMQ w przypadku usługi MSMQ. To działanie jest tworzony podczas ServiceHost.Open() i zawiera ślady związane z tworzenia i usuwania odbiornik, jak również przeniesienie się dla wszystkich działań ReceiveBytes.|  
|P|Odbieranie bajtów w połączeniu [address]. Odbieranie wiadomości usługi MSMQ.|ReceiveBytes|W przypadku tego działania przetwarzania danych, który ostatecznie zostanie wyświetlony komunikat z usługi WCF. Przychodzące bajty jest oczekiwany w przypadku transportu ukierunkowane na połączenia lub protokołu http. Dla protokołu TCP/potoków okres istnienia tego działania jest okres istnienia połączenia, jest tworzona, gdy połączenie zostanie utworzony. Dla protokołu http okres istnienia komunikatu żądania i nie jest tworzone, gdy komunikat jest wysyłany. To działanie zawiera ślady dotyczące tworzenia i usuwania połączenia, jeśli ma to zastosowanie, a także przenosi się do wszystkich działań przetwarzania komunikatu (obiekt).<br /><br /> W przypadku usługi MSMQ jest działanie gdzie wiadomości usługi MSMQ są pobierane.|  
|Q|Przetwórz komunikat [liczba]. (Uwaga: [numer] jest monotonicznie rosnący wartość, która rozpoczyna się od 1).|ProcessMessage|Przetwarzanie wiadomości przychodzących. To działanie uruchamia się po otrzymaniu wszystkich danych (w bajtach, wiadomości usługi MSMQ) w celu utworzenia obiektu komunikatów WCF. Ślady w ramach tego działania zajmuje się przetwarzanie nagłówka.<br /><br /> Po wiadomości, które mogą być wysyłane do utworzonego działania ServiceHost ProcessAction przełączy się po wyszukaniu odpowiedniego identyfikatora działania|  
|D, S|Przetwarzaj akcję "[action]".|ProcessAction|Odbieranie komunikatów za pomocą stosu transportu/Security/RM do wysyłania wiadomości do kodu użytkownika na, proces w odwrotnej kolejności niż kolejność przy wysyłaniu.<br /><br /> Na serwerze to działanie używa propagowana. identyfikator działania, jeśli jest wysyłany w nagłówku komunikatu za pośrednictwem "Propagacja działania"; w przeciwnym razie jest tworzony nowy identyfikator GUID.<br /><br /> Komunikat odpowiedzi dla kontraktów "żądanie/odpowiedź" również są przetwarzane w tym działaniu.|  
|T|Wykonaj [IContract.Operation].|ExecuteUserCode|Po wysłaniu po stronie usługi, należy wykonać kod użytkownika. To działanie zapewnia granicę, aby odróżnić ServiceHost kodu z kodu użytkownika.|  
  
## <a name="security-activities"></a>Działania dotyczące zabezpieczeń  
 Poniższa tabela zawiera listę wszystkich działań związanych z zabezpieczeniami.  
  
|Nazwa działania|Typ działania|Opis|  
|-------------------|-------------------|-----------------|  
|Konfigurowanie bezpiecznej sesji|SetupSecurity|Istnieje tylko na stronie klienta. Zawiera wszystkie RST * / SCT wymienia do uwierzytelniania i ustawienia kontekstu zabezpieczeń. Jeśli `propagateActivity` = `true`, to działanie jest scalany z usługi odpowiedniego procesu akcji RST\*/SCT działań.|  
|Zamknij bezpiecznej sesji|SetupSecurity|Występuje po stronie klienta. Zawiera wymiany komunikatów anulowania zamknięcia bezpiecznej sesji. Jeśli `propagateActivity` = `true`, to działanie jest scalany z działania procesu "Anuluj" z usługi.|  
  
 W poniższej tabeli wymieniono wszystkie działania związane z modelu COM +.  
  
|Nazwa działania|Typ działania|Opis|  
|-------------------|-------------------|-----------------|  
|Tworzenie wystąpienia modelu COM +|TransferToCOMPlus|1 wystąpienie działania dla każdego modelu COM + wywołują z kodu programu WCF|  
|Wykonaj modelu COM + \<operacji >|TransferToCOMPlus|1 wystąpienie działania dla każdego modelu COM + wywołują z kodu programu WCF|  
  
## <a name="wmi-activities"></a>Działania usługi WMI  
 Poniższa tabela zawiera listę wszystkich działań związanych z usługą WMI.  
  
|Nazwa działania|Typ działania|Opis|  
|-------------------|-------------------|-----------------|  
|Pobierz WMI|WMIGetObject|Użytkownik pobiera dane z usługi WMI.|  
|Umieść WMI|WmiPutInstance|Użytkownik jest aktualizowanie danych za pomocą usługi WMI.|
