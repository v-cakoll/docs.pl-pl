---
title: Transport MSMQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7d2b0e7e660ef90bb854309bb3dadbab55d1131f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="msmq-transport"></a>Transport MSMQ
W tym temacie wymieniono wszystkie wyjątki generowane przez usługę transportową MSMQ.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|MsmqActiveDirectoryRequiresNativeTransfer|Nie można zweryfikować powiązania dla wiadomości. Klient nie może wysłać wiadomości. Błąd został spowodowany przez konflikt we właściwościach powiązania. Właściwość UseActiveDirectory ma wartość true, a właściwość QueueTransferProtocol ma wartość Native. Aby usunąć konflikt, popraw jedną z właściwości.|  
|MsmqAuthNoneRequiresProtectionNone|Nie można zweryfikować powiązania dla usługi. Nie można uruchomić punktu końcowego usługi lub klienta. Błąd został spowodowany przez konflikt we właściwościach powiązania. Element MsmqAuthenticationMode ma wartość None, a MsmqProtectionLevel nie jest ustawiona na Brak. Aby usunąć konflikt, popraw jedną z właściwości.|  
|MsmqCustomRequiresPerAddDLQ|Nie można zweryfikować powiązania dla wiadomości. Klient nie może wysłać wiadomości. DeadLetterQueue wartość jest ustawiona na Custom, ale właściwość CustomDeadLetterQueue nie jest określony. Określ identyfikator URI kolejki utraconych wiadomości dla każdej aplikacji we właściwości CustomDeadLetterQueue.|  
|MsmqDeserializationError|Napotkano błąd podczas deserializacji komunikatu XML. Wiadomość nie może być odbierany i zostało porzucone.|  
|MsmqDLQNotWriteable|Nie można zweryfikować powiązania dla klienta. Klient nie może wysłać wiadomości. Określona kolejka utraconych wiadomości nie istnieje lub nie można zapisać. Upewnij się, że kolejka istnieje z odpowiednią autoryzacją do zapisu.|  
|MsmqGetPrivateComputerInformationError|Sprawdzenie wersji nie powiodło się z powodu określonego błędu. Nie można wykryć wersji usługi MSMQ, wszystkich operacji w kolejkowanym kanale zakończą się niepowodzeniem. Upewnij się, że usługa MSMQ jest zainstalowana i jest dostępny.|  
|MsmqNoAssurancesForVolatile|Nie można zweryfikować powiązania dla usługi. Nie można uruchomić punktu końcowego usługi lub klienta. ExactlyOnce wartość właściwości jest równa true, a właściwość Durable ma wartość false. Jest to nieobsługiwane. Aby usunąć konflikt, popraw jedną z tych właściwości.|  
|MsmqNonTransactionalQueueNeeded|Wykryto niezgodność między powiązaniem a konfiguracją kolejki usługi MSMQ. Nie można uruchomić punktu końcowego usługi. Właściwość ExactlyOnce jest ustawiona na false i odczytywane wiadomości w kolejce jest kolejką transakcyjną. Popraw błąd, ustawiając dla właściwości ExactlyOnce wartość true lub utwórz powiązanie nietransakcyjne.|  
|MsmqOpenError|Wystąpił błąd podczas otwierania określonej kolejki. Wiadomość nie może być wysyłane lub odbierane z kolejki. Upewnij się, że usługa MSMQ jest zainstalowana i uruchomiona. Upewnij się również, że kolejka jest dostępna z trybu wymagane prawa dostępu i autoryzacji.|  
|MsmqPathLookupError|Wystąpił błąd podczas konwertowania nazwy ścieżki określonej kolejki na nazwę formatu. Wszystkich operacji w kolejkowanym kanale nie powiodło się. Upewnij się, że adres kolejki jest prawidłowy. Usługa MSMQ musi zostać zainstalowana z włączoną integracją usługi Active Directory i jest dostępny do niego dostęp.|  
|MsmqPerAppDLQRequiresCustom|Nie można zweryfikować powiązania na kliencie. Klient nie może wysłać wiadomości. Właściwość CustomDeadLetterQueue jest ustawiona, ale właściwość DeadLetterQueue nie ustawiono niestandardowego. Ustaw dla właściwości DeadLetterQueue wartość niestandardowy.|  
|MsmqPerAppDLQRequiresExactlyOnce|Nie można zweryfikować powiązania dla klienta. Klient nie może wysłać wiadomości. Błąd został spowodowany przez konflikt we właściwościach powiązania. Aby używać niestandardowej kolejki utraconych wiadomości, ExactlyOnce musi mieć ustawioną wartość true, aby usunąć konflikt.|  
|MsmqPerAppDLQRequiresMsmq4|Wykryto niezgodność między powiązaniem i konfiguracją Kolejkowania. Klient nie może wysłać wiadomości. Aby używać niestandardowej kolejki utraconych wiadomości, musi mieć usługi MSMQ w wersji 4.0 lub nowszej. Jeśli nie masz usługi MSMQ w wersji 4.0 lub nowszej należy ustawić dla właściwości DeadLetterQueue wartość System lub None.|  
|MsmqReceiveError|Wystąpił błąd podczas odbierania wiadomości z kolejki. Upewnij się, że usługa MSMQ jest zainstalowana i uruchomiona. Upewnij się, że z kolejki można odbierać wiadomości.|  
|MsmqSameTransactionExpected|Wystąpił błąd transakcji dla tej sesji. Wystąpił błąd kanału sesji. Wiadomości w sesji nie może być wysyłane lub odbierane. Kolejkowana sesja nie może być skojarzony z więcej niż jednej transakcji. Upewnij się, że wszystkie wiadomości w sesji są wysyłane lub odbierane przy użyciu pojedynczej transakcji.|  
|MsmqSendError|Wystąpił błąd podczas wysyłania do określonej kolejki. Upewnij się, że usługa MSMQ jest zainstalowana i uruchomiona. W przypadku wysyłania do kolejki lokalnej upewnij się, że kolejka istnieje z trybu wymagane prawa dostępu i autoryzacja.|  
|MsmqTimeSpanTooLarge|Czas wygaśnięcia wiadomości jest za duży. Nie można wysłać wiadomości. Komunikat, czas wygaśnięcia (TTL) nie może przekraczać maksymalnej wartości Int32.|  
|MsmqTokenProviderNeededForCertificates|Nie można odnaleźć Element X509SecurityTokenProvider. Nie można wysłać wiadomości. Tryb uwierzytelniania certyfikatów wymaga dostawcy tokenów X.509. Upewnij się, że dostawcy tokenów zabezpieczających jest dostępna dla zainstalowany certyfikat.|  
|MsmqTransactedDLQExpected|Wystąpiła niezgodność między powiązaniem a konfiguracją usługi MSMQ. Nie można wysłać wiadomości. Niestandardowej kolejki utraconych wiadomości określona w powiązaniu musi być kolejką transakcji. Upewnij się, że adres niestandardowej kolejki utraconych wiadomości jest poprawny i kolejka jest kolejką transakcyjną.|  
|MsmqTransactionalQueueNeeded|Wystąpiła niezgodność między powiązaniem a konfiguracją kolejki usługi MSMQ. Nie można uruchomić punktu końcowego usługi. ExactlyOnce wartość właściwości jest równa true, a kolejka odczytywane wiadomości nie jest kolejką transakcyjną. Aby naprawić błąd, ustaw dla właściwości ExactlyOnce wartość false lub Utwórz kolejkę transakcyjną dla tego powiązania.|  
|MsmqTransactionCurrentRequired|Żadna transakcja nie jest dostępne do wysyłania wiadomości w sesji. Aby wysłać wiadomość w kolejce sesji wymaga transakcji. Upewnij się, że zakresu transakcji został określony do wysłania tej wiadomości w sesji.|  
|MsmqTransactionRequired|Transakcja jest wymagana, ale nie jest dostępna. Wiadomości nie mogą być wysyłane lub odbierane. Upewnij się, że określono zasięg transakcji, aby wysyłać lub odbierać wiadomości.|  
|MsmqUnsupportedSerializationFormat|Wystąpił błąd deserializacji. Wiadomość nie może być odbierany i zostało porzucone. Format serializacji określonego nie jest obsługiwany.|  
|MsmqWrongPrivateQueueSyntax|Adres URL jest nieprawidłowy. Adres URL kolejki nie może zawierać znaku "$". Aby zaadresować kolejkę prywatną, należy użyć składni net.msmq://machine/private/queueName.|
