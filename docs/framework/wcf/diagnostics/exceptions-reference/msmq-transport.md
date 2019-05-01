---
title: Transport MSMQ
ms.date: 03/30/2017
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
ms.openlocfilehash: a2e5384808b82f48bd1d4856bf893130da8c5f1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959422"
---
# <a name="msmq-transport"></a>Transport MSMQ
Ten temat zawiera listę wszystkich wyjątków generowanych przez usługę transportową MSMQ.  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|MsmqActiveDirectoryRequiresNativeTransfer|Nie można zweryfikować powiązania dla wiadomości. Klient nie może wysyłać wiadomości. Konflikt we właściwościach powiązania przyczyną tego błędu. UseActiveDirectory ma wartość TRUE i ustawiono właściwość QueueTransferProtocol Native. Aby rozwiązać konflikt, popraw jedna z właściwości.|  
|MsmqAuthNoneRequiresProtectionNone|Nie można zweryfikować powiązania dla usługi. Nie można uruchomić punktu końcowego usługi lub klienta. Konflikt we właściwościach powiązania przyczyną tego błędu. MsmqAuthenticationMode ma wartość None i MsmqProtectionLevel nie jest ustawiona na wartość None. Aby rozwiązać konflikt, popraw jedną z właściwości.|  
|MsmqCustomRequiresPerAddDLQ|Nie można zweryfikować powiązania dla wiadomości. Klient nie może wysłać komunikatu. DeadLetterQueue wartość został ustawiony niestandardowy, ale nie określono CustomDeadLetterQueue. Określ identyfikator URI kolejki utraconych wiadomości dla każdej aplikacji we właściwości CustomDeadLetterQueue.|  
|MsmqDeserializationError|Napotkano błąd podczas deserializacji komunikatu XML. Komunikat nie może być odbierany i zostało porzucone.|  
|MsmqDLQNotWriteable|Nie można zweryfikować powiązania dla klienta. Klient nie może wysłać wiadomość. Określonej kolejki utraconych wiadomości nie istnieje lub nie mogą być zapisywane. Sprawdź, czy kolejka istnieje z odpowiednią autoryzacją do zapisu do nich.|  
|MsmqGetPrivateComputerInformationError|Sprawdzenie wersji nie powiodło się z powodu określonego błędu. Nie można wykryć wersji MSMQ, wszystkie operacje, które znajdują się w kolejce kanału zakończą się niepowodzeniem. Upewnij się, że usługa MSMQ jest zainstalowana i jest dostępna.|  
|MsmqNoAssurancesForVolatile|Nie można zweryfikować powiązania dla usługi. Nie można uruchomić punktu końcowego usługi lub klienta. Właściwość jest ustawiona na true, a właściwość trwałe ExactlyOnce ma wartość false. Jest to nieobsługiwane. Aby rozwiązać konflikt, usuń jedną z tych właściwości.|  
|MsmqNonTransactionalQueueNeeded|Wykryto niezgodność między powiązaniem i konfiguracją kolejki usługi MSMQ. Nie można uruchomić punktu końcowego usługi. Właściwość ExactlyOnce jest ustawiona na false i odczytywać komunikaty z kolejki jest kolejką transakcyjną. Popraw błąd, ustawiając właściwość ExactlyOnce wartość true, lub utwórz powiązanie nietransakcyjnej.|  
|MsmqOpenError|Wystąpił błąd podczas otwierania określonej kolejki. Komunikat nie mogą być wysyłane lub odbierane z kolejki. Upewnij się, że usługa MSMQ jest zainstalowana i uruchomiona. Upewnij się również, że kolejka jest dostępna, aby otworzyć tryb wymagane prawa dostępu i autoryzacji.|  
|MsmqPathLookupError|Wystąpił błąd podczas konwertowania nazwa ścieżki kolejki określona nazwa formatu. Wszystkie operacje w kolejce kanału nie powiodło się. Upewnij się, że adres kolejki jest prawidłowy. Usługa MSMQ musi być zainstalowany z włączoną integracją usługi Active Directory i dostęp do niego jest możliwy.|  
|MsmqPerAppDLQRequiresCustom|Nie można zweryfikować powiązania, na komputerze klienckim. Klient nie może wysyłać wiadomości. Właściwość CustomDeadLetterQueue jest ustawiona, ale nie ustawiono właściwość DeadLetterQueue niestandardowy. Ustaw właściwość DeadLetterQueue niestandardowy.|  
|MsmqPerAppDLQRequiresExactlyOnce|Nie można zweryfikować powiązania dla klienta. Klient nie może wysyłać wiadomości. Konflikt we właściwościach powiązania powoduje awarię. Aby użyć niestandardowego kolejki utraconych wiadomości, ExactlyOnce musi być równa true, aby rozwiązać konflikt.|  
|MsmqPerAppDLQRequiresMsmq4|Wykryto niezgodność między powiązaniem i konfiguracji MSMQ. Klient nie może wysyłać wiadomości. Aby użyć niestandardowego kolejki utraconych wiadomości, konieczne jest posiadanie usługi MSMQ w wersji 4.0 lub nowszej. Jeśli nie masz usługi MSMQ w wersji 4.0 lub nowszej należy ustawić właściwość DeadLetterQueue System lub None.|  
|MsmqReceiveError|Wystąpił błąd podczas odbierania wiadomości z kolejki. Upewnij się, że usługa MSMQ jest zainstalowana i uruchomiona. Upewnij się, że można odbierać wiadomości z kolejki.|  
|MsmqSameTransactionExpected|Wystąpił błąd transakcji dla tej sesji. Wystąpił błąd kanału sesji. Wiadomości w sesji nie mogą być wysyłane lub odbierane. Sesję w kolejce nie może być skojarzony z więcej niż jedna transakcja. Upewnij się, że wszystkie komunikaty w sesji są wysyłane lub odebranych przy użyciu jednej transakcji.|  
|MsmqSendError|Wystąpił błąd podczas wysyłania do określonej kolejki. Upewnij się, że usługa MSMQ jest zainstalowana i uruchomiona. W przypadku wysyłania kolejka lokalna, upewnij się, że kolejka istnieje z trybu wymagane prawa dostępu i autoryzacja.|  
|MsmqTimeSpanTooLarge|Czas wygaśnięcia komunikatu jest zbyt duży. Nie można wysłać wiadomości. Komunikat, czas wygaśnięcia (TTL) nie może przekroczyć maksymalnej wartości Int32.|  
|MsmqTokenProviderNeededForCertificates|Nie można odnaleźć Element X509SecurityTokenProvider. Nie można wysłać wiadomości. Tryb uwierzytelniania certyfikatu wymaga dostawcę tokenu X.509. Upewnij się, że dostawcy tokenów zabezpieczeń jest dostępne dla zainstalowanych certyfikatów.|  
|MsmqTransactedDLQExpected|Wystąpiła niezgodność między powiązaniem i konfiguracji MSMQ. Nie można wysłać wiadomości. Niestandardowe kolejki utraconych wiadomości określonej w powiązaniu musi być Kolejka transakcji. Upewnij się, że adres niestandardowej kolejki utraconych wiadomości jest poprawny, i kolejka jest kolejką transakcyjną.|  
|MsmqTransactionalQueueNeeded|Wystąpiła niezgodność między powiązaniem i konfiguracją kolejki usługi MSMQ. Nie można uruchomić punktu końcowego usługi. ExactlyOnce właściwości ustawiono wartość true jak i kolejka odczytywanie komunikatów z nie jest kolejką transakcyjną. Aby rozwiązać ten problem, aby wskazywał błąd, należy ustawić wartość false dla właściwości ExactlyOnce lub Utwórz kolejkę transakcyjną dla tego powiązania.|  
|MsmqTransactionCurrentRequired|Żadna transakcja nie jest dostępne do wysyłania komunikatów w sesji. Aby wysłać wiadomość w kolejce sesji wymaga transakcji. Upewnij się, że zakres transakcji został określony do wysłania wiadomości w sesji.|  
|MsmqTransactionRequired|Transakcja jest wymagany, ale nie jest dostępna. Komunikaty nie mogą być wysyłane lub odbierane. Upewnij się, że zakres transakcji został określony do wysyłania i odbierania wiadomości.|  
|MsmqUnsupportedSerializationFormat|Wystąpił błąd deserializacji. Komunikat nie może być odbierany i zostało porzucone. Format serializacji określonego nie jest obsługiwany.|  
|MsmqWrongPrivateQueueSyntax|Adres URL jest nieprawidłowy. Adres URL kolejki nie może zawierać znaku "$". Aby rozwiązać kolejki prywatnej, należy użyć składni net.msmq://machine/private/queueName.|
