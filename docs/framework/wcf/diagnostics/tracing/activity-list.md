---
title: Lista działań
ms.date: 03/30/2017
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
ms.openlocfilehash: f96aab037e86b05096df7ffc82a0be3f6cce1ad2
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809761"
---
# <a name="activity-list"></a>Lista działań
Ten temat zawiera listę wszystkich działań, które są zdefiniowane przez Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Działania można również definiować programowo do grupy użytkowników śladów. Aby uzyskać więcej informacji, zobacz [emitowanie danych śledzenia User-Code](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
## <a name="servicemodel-activities"></a>Działania elementu ServiceModel  
 W poniższej tabeli wymieniono wszystkie operacje dla scenariuszy użycia głównych.  
  
|Etykieta|Nazwa działania|Typ działania|Opis|  
|-----------|-------------------|-------------------|-----------------|  
|M,|Działanie otoczenia|N/d (to nie są kontrolowane przez ServiceModel)|Działanie, którego identyfikator jest ustawione w protokole TLS przed wszelkie wywołania kodu ServiceModel (po stronie klienta lub po stronie serwera).<br /><br /> Przykład: Gdzie Otwórz wywołano klienta WCF lub serviceHost.open działania jest wywoływana.|  
|B|Konstrukcja<br /><br /> Obiekt ChannelFactory. ContractType: "[typ]".|Konstrukcja||  
|C|Otwarcie<br /><br /> [Element ClientBase&#124;ChannelFactory]. ContractType: "[typ]".|Otwarcie||  
|I|Zamknij [obiektu ClientBase&#124;ChannelFactory]. ContractType: "[typ]".|Zamknięcie||  
|M|Konstruować ServiceHost. Typ ServiceType: "[typ]".|Konstrukcja||  
|N|Otwórz element ServiceHost. Typ ServiceType: "[typ]".|Otwarcie||  
|Z|Zamknij ServiceHost. Typ ServiceType: "[typ]".|Zamknięcie||  
|O|Nasłuchiwanie na [address].|ListenAt|To i następnego działania są specyficzne dla transportu. Działanie ListenAt reprezentuje zawartość, który jest mapowany na adres, na którym nasłuchuje odbiornik kanału w. W przypadku usługi MSMQ jest samej kolejki, ponieważ kolejka jest mapowany na jeden adres. To działanie nasłuchuje połączeń przychodzących w przypadku transportu z nawiązaniem połączenia, wiadomości usługi MSMQ w przypadku usługi MSMQ. To działanie jest tworzona podczas ServiceHost.Open() i zawiera dane dotyczące tworzenia i usuwania odbiornik, jak również przesyłania wychodzących dla wszystkich działań ReceiveBytes śledzenia.|  
|P|Odbieranie bajtów w połączeniu "[address]". Odbieranie wiadomości MSMQ.|ReceiveBytes|W przypadku tego działania przetwarzania danych, który ostatecznie zostanie wyświetlony komunikat WCF. Przychodzące bajty są oczekiwano w przypadku transportu z nawiązaniem połączenia lub protokołu http. Dla protokołu TCP/nazwanego potoku okres istnienia tego działania jest okres istnienia połączenia jest tworzony, gdy połączenie jest tworzony. Dla protokołu http okres istnienia komunikatu żądania i nie jest tworzony, gdy komunikat jest wysyłany. To działanie zawiera ślady dotyczące tworzenia i usuwania połączenia, jeśli ma to zastosowanie, a także przesyła wychodzących dla wszystkich działań przetwarzanie komunikatu (obiekt).<br /><br /> W przypadku usługi MSMQ jest działanie której są pobierane wiadomości MSMQ.|  
|Q|Proces komunikatu [numer]. (Uwaga: [numer] jest monotonicznie rosnący wartość, która rozpoczyna się od 1).|ProcessMessage|Przetwarzanie wiadomości przychodzących. To działanie uruchamia się po odebraniu wszystkich danych (w bajtach, wiadomości MSMQ) do utworzenia obiektu wiadomości WCF. Dane śledzenia w obrębie tego działania zajmuje się przetwarzanie nagłówka.<br /><br /> Po jest sformatowany komunikat, który można wysłać, działanie ServiceHost ProcessAction jest przełączenie na po wyszukiwania odpowiedni identyfikator działania|  
|D-S|Przetwarzaj akcję [action].|ProcessAction|Proces otrzymywać wiadomości przez stos RM-transportu/zabezpieczeń na potrzeby rozsyłania komunikatów do kodu użytkownika na, i w odwrotnej kolejności podczas wysyłania.<br /><br /> Na serwerze to działanie używa propagowany identyfikator działania, jeśli jest wysyłany w nagłówku komunikatu za pośrednictwem "Działania propagacji"; w przeciwnym razie jest tworzony nowy identyfikator GUID.<br /><br /> Komunikat odpowiedzi dla kontraktów żądanie i odpowiedź jest również przetwarzane w danego działania.|  
|T|Wykonanie [IContract.Operation].|ExecuteUserCode|Po wysłaniu na stronie usługi na wykonanie kodu użytkownika. To działanie umożliwia granicę odróżniać ServiceHost kodu z kodu użytkownika.|  
  
## <a name="security-activities"></a>Działania dotyczące zabezpieczeń  
 W poniższej tabeli wymieniono wszystkie działania związane z zabezpieczeniami.  
  
|Nazwa działania|Typ działania|Opis|  
|-------------------|-------------------|-----------------|  
|Instalator bezpiecznej sesji|SetupSecurity|Istnieje po stronie klienta tylko. Zawiera wszystkie RST * / SCT wymiany uwierzytelniania i ustawienia kontekstu zabezpieczeń. Jeśli `propagateActivity` = `true`, to działanie jest scalany z odpowiedniego RST działania procesu usługi\*/SCT działań.|  
|Zamknij bezpiecznej sesji|SetupSecurity|Istnieje po stronie klienta. Zawiera wymiany wiadomości anulowania zamknięcia bezpiecznej sesji. Jeśli `propagateActivity` = `true`, to działanie jest scalany z akcji procesu "Anuluj" z usługi.|  
  
 W poniższej tabeli wymieniono wszystkie działania związane z modelu COM +.  
  
|Nazwa działania|Typ działania|Opis|  
|-------------------|-------------------|-----------------|  
|Utwórz wystąpienie modelu COM +|TransferToCOMPlus|Wywołaj 1 wystąpienia działania każdego modelu COM + z kodu WCF|  
|Wykonanie COM + \<operacji >|TransferToCOMPlus|Wywołaj 1 wystąpienia działania każdego modelu COM + z kodu WCF|  
  
## <a name="wmi-activities"></a>Działania usługi WMI  
 Poniższa tabela zawiera listę wszystkich działań związanych z usługą WMI.  
  
|Nazwa działania|Typ działania|Opis|  
|-------------------|-------------------|-----------------|  
|WMI get|WMIGetObject|Użytkownik pobiera dane z usługi WMI.|  
|Umieść WMI|WmiPutInstance|Użytkownik jest aktualizowanie danych za pomocą usługi WMI.|
