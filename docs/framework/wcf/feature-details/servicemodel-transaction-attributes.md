---
title: Atrybuty transakcji elementu ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel attributes
ms.assetid: 1e0d2436-6ae5-439b-9765-a448d6f60000
ms.openlocfilehash: 8f8a50dc82c073c9357209a4dbeeed6c8b075695
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586145"
---
# <a name="servicemodel-transaction-attributes"></a>Atrybuty transakcji elementu ServiceModel
Windows Communication Foundation (WCF) udostępnia właściwości na trzech standardowych <xref:System.ServiceModel> atrybutów, które umożliwiają skonfigurowanie zachowanie transakcji usługi WCF:  
  
- <xref:System.ServiceModel.TransactionFlowAttribute>  
  
- <xref:System.ServiceModel.ServiceBehaviorAttribute>  
  
- <xref:System.ServiceModel.OperationBehaviorAttribute>  
  
## <a name="transactionflowattribute"></a>TransactionFlowAttribute  
 <xref:System.ServiceModel.TransactionFlowAttribute> Atrybut określa gotowość operacji kontraktu usługi do akceptowania przychodzących transakcji od klienta. Ten atrybut zawiera tę kontrolkę z następującymi właściwościami: Użyj transakcji <xref:System.ServiceModel.TransactionFlowOption> wyliczeniu, aby określić, czy transakcja przychodzących jest <xref:System.ServiceModel.TransactionFlowOption.Mandatory>, <xref:System.ServiceModel.TransactionFlowOption.Allowed>, lub <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.  
  
 Jest to jedyny atrybut, które odnoszą się operacji usługi do zewnętrznego interakcji z klientem. Atrybutów opisanych w poniższych sekcjach odnoszą się do korzystania z transakcji w ramach wykonywania operacji.  
  
## <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute  
 <xref:System.ServiceModel.ServiceBehaviorAttribute> Atrybut określa zachowanie wykonywania wewnętrznej implementacji kontraktu usługi. Właściwości specyficzne dla transakcji tego atrybutu to:  
  
- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> Określa, czy do ukończenia niedokończonej transakcji po zamknięciu sesji. Wartość domyślna tej właściwości to `false`. Jeśli ta właściwość jest `true`i Przychodząca sesja została zostanie poprawnie zamknięte zamiast zamykania, ze względu na klienta lub sieci, błędy, pomyślnym zakończeniu dowolnej niewykonanej transakcji. W przeciwnym razie, jeśli ta właściwość jest `false` lub jeśli sesja nie została zamknięta bez problemu zmieniała, dowolnej niewykonanej transakcji jest wycofywany, a po zamknięciu sesji. Jeśli ta właściwość jest `true`, kanałów przychodzących muszą być oparte na sesji.  
  
- <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> Określa, czy podstawowe wystąpienie usługi jest wydane po zakończeniu transakcji. Wartość domyślna tej właściwości to `true`. Następny komunikat przychodzący powoduje, że nowe wystąpienie bazowego ma zostać utworzony, odrzucając stan każdej transakcji, który mogą być przechowywane poprzednie wystąpienie. Zwalnianie wystąpienie usługi jest akcję wewnętrzną usługę przyjmuje i nie ma wpływu na istniejące połączenia ani sesje, które klienci mogą utworzone. Ta funkcja jest odpowiednikiem funkcji aktywacji just-in-time, udostępnia modelu COM +. Jeśli właściwość jest `true`, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> musi być równa <xref:System.ServiceModel.ConcurrencyMode.Single>. W przeciwnym razie usługa zgłasza wyjątek nieprawidłowa konfiguracja sprawdzania poprawności podczas uruchamiania.  
  
- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> Określa poziom izolacji dla transakcji w ramach usługi; Ta właściwość ma jedną z <xref:System.Transactions.IsolationLevel> wartości. Jeśli jest coś innego niż właściwość poziomu izolacji lokalnego <xref:System.Transactions.IsolationLevel.Unspecified>, poziom izolacji transakcji przychodzących musi odpowiadać ustawienie tej właściwości lokalnej. W przeciwnym razie transakcji jest odrzucana i błędów są wysyłane z powrotem do klienta. Jeśli <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> jest `true`, i braku transakcji jest przepływ, ta właściwość określa <xref:System.Transactions.IsolationLevel> wartość używaną dla transakcji utworzone lokalnie. Jeśli <xref:System.Transactions.IsolationLevel> ustawiono <xref:System.Transactions.IsolationLevel.Unspecified>, <xref:System.Transactions.IsolationLevel> <xref:System.Transactions.IsolationLevel.Serializable> jest używany.  
  
- <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> Określa okres czasu, w którym należy wykonać nową transakcję utworzono usługę. Jeśli ten czas, a transakcja nie została zakończona, zostanie przerwany. <xref:System.TimeSpan> Służy jako <xref:System.Transactions.TransactionScope> limitu czasu dla wszystkich operacji, które mają <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> równa `true` i dla którego utworzono nową transakcję. Limit czasu jest maksymalny dozwolony czas trwania od utworzenia transakcji do wykonania fazy 1 w dwufazowy protokół zatwierdzania. Wartość limitu czasu, używana jest zawsze niższą wartość między <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> właściwości i `transactionTimeout` ustawienia konfiguracji.  
  
## <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute  
 <xref:System.ServiceModel.OperationBehaviorAttribute> Atrybut określa rodzajami zachowań tych metod w implementacji usługi. Służy do wskazania zachowanie wykonywania określonych operacji. Właściwości tego atrybutu nie ma wpływu na opis kontraktu usługi Web Service Description Language (WSDL) i są wyłącznie te elementy modelu programowania usługi WCF, które włączają typowe funkcje, w przeciwnym razie deweloperzy muszą implementować samodzielnie.  
  
 Ten atrybut ma następujące właściwości specyficzne dla transakcji:  
  
- <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Określa, czy metoda muszą być wykonywane w zakresie aktywnej transakcji. Wartość domyślna to `false`. Jeśli <xref:System.ServiceModel.OperationBehaviorAttribute> atrybut nie jest ustawiony dla metody, również oznacza, że metody nie będą wykonywane w ramach transakcji. Jeśli zakres transakcji nie jest wymagane dla danej operacji, każdą transakcję, która znajduje się w nagłówku komunikatu nie została aktywowana i pozostaje jako element <xref:System.ServiceModel.OperationContext.IncomingMessageProperties%2A> z <xref:System.ServiceModel.OperationContext>. Jeśli zakres transakcji jest wymagane dla danej operacji, źródła dla transakcji jest tworzony na podstawie jednej z następujących czynności:  
  
    - Jeśli transakcja jest przekazane przez klienta, metoda jest wykonywana w ramach zakresu transakcji utworzone za pomocą tej transakcji rozproszonej.  
  
    - Za pomocą transportu umieszczonych w kolejce transakcji, używane do usuwania z kolejki wiadomości jest używany. Należy zauważyć, że używane w transakcji nie jest przesłanej transakcji, w tym, że nie został dostarczony przez oryginalnego nadawcy wiadomości.  
  
    - Niestandardowe transportu może zapewnić transakcji za pośrednictwem `TransportTransactionProperty`.  
  
    - Jeśli żadne z powyższych udostępnia zewnętrznego źródła dla transakcji to nowy <xref:System.Transactions.Transaction> tworzone jest wystąpienie bezpośrednio przed wywołaniem metody.  
  
- <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> Określa, czy transakcji, w którym metoda jest wykonywana jest wprowadzana automatycznie, jeśli nie nieobsłużone wyjątki są zgłaszane. Jeśli ta właściwość jest `true`, wywoływania infrastruktury automatycznie oznacza transakcji jako "ukończone", jeśli metoda użytkownika jest zwracane bez zostanie zgłoszony wyjątek. Jeśli ta właściwość jest `false`, transakcja jest dołączony do wystąpienia, a tylko jest oznaczony jako "ukończone", jeśli klient wywołuje kolejnych metodę, która jest oznaczona za pomocą tej właściwości równa `true`, czy metoda kolejnych wywołań jawnie <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>. Nie można wykonać jedną z tych wersji wyniki w transakcji, nigdy nie jest "ukończone", a zawarte pracy nie zostanie zatwierdzony, chyba że <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> właściwość jest ustawiona na `true`. Jeśli ta właściwość jest ustawiona `true`, należy użyć kanału w sesji i <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> musi być równa <xref:System.ServiceModel.InstanceContextMode.PerSession>.
