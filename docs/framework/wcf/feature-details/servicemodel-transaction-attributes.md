---
title: Atrybuty transakcji elementu ServiceModel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], ServiceModel attributes
ms.assetid: 1e0d2436-6ae5-439b-9765-a448d6f60000
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08ebb19cb7fab8221ac1eb534777afffa0bad328
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="servicemodel-transaction-attributes"></a>Atrybuty transakcji elementu ServiceModel
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Udostępnia właściwości na standardzie trzy <xref:System.ServiceModel> atrybuty, które umożliwiają konfigurowanie zachowania transakcji dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi:  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute>  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute>  
  
## <a name="transactionflowattribute"></a>TransactionFlowAttribute  
 <xref:System.ServiceModel.TransactionFlowAttribute> Atrybut określa gotowość operacji w kontrakcie usługi do akceptowania przychodzących transakcji od klienta. Ten atrybut zapewnia tego formantu z następującej właściwości: Użyj transakcji <xref:System.ServiceModel.TransactionFlowOption> wyliczeniu, aby określić, czy jest transakcji przychodzącej <xref:System.ServiceModel.TransactionFlowOption.Mandatory>, <xref:System.ServiceModel.TransactionFlowOption.Allowed>, lub <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.  
  
 Jest to jedyny atrybut związanego z operacji usługi do zewnętrznego interakcji z klientem. Atrybuty opisane w poniższych sekcjach są powiązane z użyciem transakcji w ramach wykonywania operacji.  
  
## <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute  
 <xref:System.ServiceModel.ServiceBehaviorAttribute> Atrybut określa sposób wykonywania wewnętrznej implementacji kontraktu usługi. Właściwości specyficzne dla transakcji tego atrybutu to:  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A>Określa, czy do zrealizowania transakcji niezakończona, po zamknięciu sesji. Wartość domyślna dla tej właściwości to `false`. Jeśli ta właściwość jest `true`i Przychodząca sesja bezpiecznie został zamknięty zamiast zamknięcia z powodu sieci lub klienta błędów, zakończy się pomyślnie wszystkie niezakończone transakcji. W przeciwnym razie, jeśli ta właściwość jest `false` lub jeśli sesja nie został zamknięty bezpiecznie, każdej transakcji niezakończona została wycofana przy zamknięciu sesji. Jeśli ta właściwość jest `true`, kanał przychodzący muszą być oparte na sesji.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A>Określa, czy źródłowy wystąpienie usługi jest zwolnione po zakończeniu transakcji. Wartość domyślna dla tej właściwości to `true`. Następny komunikat przychodzący powoduje, że nowe wystąpienie źródłowy ma zostać utworzony, odrzucając stan każdej transakcji poprzednie wystąpienie może mieć przechowywane. Udostępnia wystąpienie usługi jest czynnością wewnętrzny usługi trwa i nie ma wpływu na istniejące połączenia ani sesje, które może być utworzone klientów. Ta funkcja jest odpowiednikiem COM + zawiera funkcja aktywacji just in time. Jeśli właściwość jest `true`, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> musi być równa <xref:System.ServiceModel.ConcurrencyMode.Single>. W przeciwnym razie usługa zgłasza wyjątek weryfikacji nieprawidłową konfigurację podczas uruchamiania.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>Określa poziom izolacji dla transakcji w ramach usługi; Ta właściwość ma jeden z <xref:System.Transactions.IsolationLevel> wartości. Jeśli właściwość poziomu izolacji lokalnego jest inna innych niż <xref:System.Transactions.IsolationLevel.Unspecified>, poziom izolacji transakcji przychodzącej musi być zgodna z ustawienia tej właściwości lokalnej. W przeciwnym razie transakcji przychodzącej został odrzucony, a błąd są wysyłane do klienta. Jeśli <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> jest `true`, a żadna transakcja nie jest umieszczane, ta właściwość określa <xref:System.Transactions.IsolationLevel> wartość dla transakcji utworzony lokalnie. Jeśli <xref:System.Transactions.IsolationLevel> ustawiono <xref:System.Transactions.IsolationLevel.Unspecified>, <xref:System.Transactions.IsolationLevel> <xref:System.Transactions.IsolationLevel.Serializable> jest używany.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>Określa okres czasu, w którym należy wykonać nową transakcję utworzono usługę. Jeśli teraz, a transakcja nie została ukończona, zostanie przerwane. <xref:System.TimeSpan> Jest używany jako <xref:System.Transactions.TransactionScope> limitu czasu dla wszystkich operacji, które mają <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> ustawioną `true` i dla którego utworzono nową transakcję. Limit czasu jest maksymalny dozwolony czas trwania od utworzenia transakcji do wykonania fazy 1 dwufazowego protokołu wykonania. Wartość limitu czasu, używana jest zawsze niższą wartość między <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> właściwości i `transactionTimeout` ustawienia konfiguracji.  
  
## <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute  
 <xref:System.ServiceModel.OperationBehaviorAttribute> Atrybut określa zachowania metod w implementacji usługi. Służy on do wskazują sposób wykonywania określonej operacji. Właściwości dla tego atrybutu nie wpływają na opis kontraktu usługi Web Service Description Language (WSDL) oraz czy czysto elementy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelu programowania, które umożliwiają typowe funkcje, które w przeciwnym razie programiści muszą implementować samodzielnie.  
  
 Ten atrybut ma następujące właściwości specyficzne dla transakcji:  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>Określa, czy metoda musi być wykonywany w obrębie aktywnej transakcji. Wartość domyślna to `false`. Jeśli <xref:System.ServiceModel.OperationBehaviorAttribute> atrybut nie jest ustawiony dla metody, również oznacza, że metoda nie zostanie wykonany w transakcji. Jeśli zakresu transakcji nie jest wymagana do wykonania operacji, każdą transakcję, która znajduje się w nagłówku komunikatu nie została aktywowana i pozostaje jako element <xref:System.ServiceModel.OperationContext.IncomingMessageProperties%2A> z <xref:System.ServiceModel.OperationContext>. Jeśli zakresu transakcji jest wymagana do wykonania operacji, źródło transakcji pochodzi z jednego z następujących czynności:  
  
    -   Jeśli transakcja jest umieszczane od klienta, metoda jest wykonywane w ramach zakresu transakcji utworzone za pomocą tej transakcji rozproszonej.  
  
    -   Za pomocą transportu umieszczonych w kolejce transakcja używana do usuwania z kolejki wiadomości jest używany. Należy pamiętać, że używane w transakcji nie jest przesłanej transakcji, że nie została podana przez adres oryginalnego nadawcy wiadomości.  
  
    -   Niestandardowe transportu można podać transakcji za pośrednictwem `TransportTransactionProperty`.  
  
    -   Jeśli żaden z powyższych udostępnia źródła zewnętrznego dla transakcji, nowy <xref:System.Transactions.Transaction> bezpośrednio przed wywołaniem metody jest tworzone wystąpienie.  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>Określa, czy transakcja, w której wykonuje metodę jest wprowadzana automatycznie, jeśli nie nieobsługiwane wyjątki są zgłaszane. Jeśli ta właściwość jest `true`, wywołujący infrastruktury automatycznie oznacza transakcji jako "ukończone", jeśli metoda użytkownika zwraca bez generowania wyjątku. Jeśli ta właściwość jest `false`, transakcja jest dołączony do wystąpienia, a tylko jest oznaczone jako "ukończone", jeśli klient wywołuje metodę kolejnych oznaczonej za pomocą tej właściwości równa `true`, lub jeśli kolejne metoda jawnie wywołuje <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>. Nie można wykonać jedną z tych wyników w ramach transakcji jest "zakończyła się nigdy", i zawartych w niej pracy nie została przekazana, chyba że <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> właściwość jest ustawiona na `true`. Jeśli ta właściwość jest ustawiona na `true`, należy użyć kanału z sesji i <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> musi mieć ustawioną <xref:System.ServiceModel.InstanceContextMode.PerSession>.
