---
title: Lista działań
ms.date: 03/30/2017
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
ms.openlocfilehash: d048dc9851a3b07b6c7457de95f2c752b0ffa964
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933580"
---
# <a name="activity-list"></a>Lista działań
W tym temacie wymieniono wszystkie działania zdefiniowane przez Windows Communication Foundation (WCF).  
  
> [!NOTE]
> Możesz również programowo definiować działania, aby grupować ślady użytkowników. Aby uzyskać więcej informacji, zobacz [emitowanie śladów kodu użytkownika](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
## <a name="servicemodel-activities"></a>Działania ServiceModel  
 W poniższej tabeli wymieniono wszystkie działania dotyczące głównych scenariuszy użycia.  
  
|Etykieta|Nazwa działania|Typ działania|Opis|  
|-----------|-------------------|-------------------|-----------------|  
|A, M|Działanie otoczenia|Nie dotyczy (to nie jest kontrolowane przez ServiceModel)|Działanie, którego identyfikator jest ustawiony w protokole TLS przed dowolnymi wywołaniami kodu ServiceModel (po stronie klienta lub po stronie serwera).<br /><br /> Przykład: Działanie, w którym jest wywoływana funkcja Otwórz na kliencie WCF lub ServiceHost. Open jest wywoływana.|  
|B|Konstrukcja<br /><br /> Endpoint. ContractType: ' [Type] '.|Konstrukcja||  
|C|Otwarcie<br /><br /> [ClientBase&#124;ChannelFactory]. ContractType: ' [Type] '.|Otwarcie||  
|I|Zamknij [element&#124;ChannelFactory elementu ClientBase]. ContractType: ' [Type] '.|Zamknięcie||  
|M|Konstruowanie ServiceHost. ServiceType: "[Type]".|Konstrukcja||  
|N|Otwórz element ServiceHost. ServiceType: "[Type]".|Otwarcie||  
|Z|Zamknij element ServiceHost. ServiceType: "[Type]".|Zamknięcie||  
|O|Nasłuchiwanie na "[address]".|ListenAt|To i następne działanie są specyficzne dla transportu. Działanie ListenAt reprezentuje zawartość, która jest mapowana na adres, w którym odbiornik kanału nasłuchuje. W przypadku usługi MSMQ jest to kolejka, ponieważ kolejka mapuje na jeden adres. To działanie nasłuchuje połączeń przychodzących w przypadku transportów ukierunkowanych na połączenia w przypadku komunikatów usługi MSMQ w przypadku usługi MSMQ. To działanie jest tworzone podczas działania ServiceHost. Open () i zawiera ślady związane z tworzeniem i usuwaniem odbiornika, a także transferem do wszystkich działań ReceiveBytes.|  
|P|Odbieraj bajty na połączeniu "[address]". Odbierz komunikat usługi MSMQ.|ReceiveBytes|W tym działaniu dane, które ostatecznie otrzymają komunikat WCF, są przetwarzane. Przychodzące bajty są oczekiwane w przypadku transportu zorientowanego na połączenia lub http. W przypadku protokołu TCP/nazwanego potoku okres istnienia tego działania to okres istnienia połączenia, który jest tworzony podczas tworzenia połączenia. W przypadku protokołu HTTP jest okres istnienia żądania komunikatu i jest tworzony podczas wysyłania wiadomości. To działanie zawiera ślady związane z tworzeniem i usuwaniem połączenia, jeśli ma zastosowanie, a także transferem do wszystkich działań przetwarzania komunikatów (obiektów).<br /><br /> W przypadku usługi MSMQ jest to działanie, w którym zostanie pobrany komunikat usługi MSMQ.|  
|Q|Komunikat procesu [Number]. (Uwaga: [Number] to monotonicznie rosnąca wartość, która zaczyna się od 1).|ProcessMessage|Przetwórz komunikat przychodzący. To działanie jest uruchamiane, gdy zostaną odebrane wszystkie dane (bajty, komunikaty MSMQ) w celu utworzenia obiektu wiadomości WCF. Ślady w ramach tego działania dotyczą przetwarzania nagłówków.<br /><br /> Po utworzeniu komunikatu, który może zostać wysłany, działanie ProcessAction ServiceHost zostanie przełączone do po wyszukaniu odpowiedniego identyfikatora działania.|  
|D, S|Przetwarzaj akcję "[Action]".|ProcessAction|Przetwórz komunikat przy użyciu stosu Transport/Security/RM w celu wysłania wiadomości do kodu użytkownika przy odbiorze i w odwrotnej kolejności przy wysyłaniu.<br /><br /> Na serwerze to działanie używa propagowanego identyfikatora działania, jeśli jest wysyłany w nagłówku wiadomości za pośrednictwem "propagacji aktywności"; w przeciwnym razie zostanie utworzony nowy identyfikator GUID.<br /><br /> Komunikat odpowiedzi dla kontraktów żądania/odpowiedzi jest również przetwarzany w ramach tego działania.|  
|T|Wykonanie operacji "[IContract. Operation]".|ExecuteUserCode|Po stronie usługi wykonaj kod użytkownika. To działanie zapewnia granicę odróżnić kodu ServiceHost z kodu dostarczonego przez użytkownika.|  
  
## <a name="security-activities"></a>Działania dotyczące zabezpieczeń  
 W poniższej tabeli wymieniono wszystkie działania związane z zabezpieczeniami.  
  
|Nazwa działania|Typ działania|Opis|  
|-------------------|-------------------|-----------------|  
|Skonfiguruj bezpieczną sesję|SetupSecurity|Istnieje tylko po stronie klienta. Zawiera wszystkie wartości RST */SCT na potrzeby uwierzytelniania i ustawiania kontekstu zabezpieczeń. Jeśli `propagateActivity` =\*to działanie zostanie scalone z odpowiadającą jej akcją procesu, RST/SCT działania. `true`|  
|Zamknij bezpieczną sesję|SetupSecurity|Istnieje po stronie klienta. Zawiera komunikat o anulowaniu wymiany wiadomości na potrzeby zamykania bezpiecznej sesji. Jeśli `propagateActivity` todziałaniezostanie`true`scalone z akcją procesu "Anuluj" z usługi. =|  
  
 W poniższej tabeli wymieniono wszystkie działania związane z modelem COM+.  
  
|Nazwa działania|Typ działania|Opis|  
|-------------------|-------------------|-----------------|  
|Utwórz wystąpienie modelu COM+|TransferToCOMPlus|1 wystąpienie działania dla każdego wywołania modelu COM+ z kodu WCF|  
|Wykonaj > \<operacji com+|TransferToCOMPlus|1 wystąpienie działania dla każdego wywołania modelu COM+ z kodu WCF|  
  
## <a name="wmi-activities"></a>Działania usługi WMI  
 W poniższej tabeli wymieniono wszystkie działania związane z usługą WMI.  
  
|Nazwa działania|Typ działania|Opis|  
|-------------------|-------------------|-----------------|  
|Pobieranie usługi WMI|WMIGetObject|Użytkownik pobiera dane z usługi WMI.|  
|Usługa WMI Put|WmiPutInstance|Użytkownik aktualizuje dane za pomocą usługi WMI.|
