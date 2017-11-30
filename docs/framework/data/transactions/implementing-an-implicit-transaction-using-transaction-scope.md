---
title: "Implementowanie transakcji niejawnej przy użyciu zakresu transakcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 49d1706a-1e0c-4c85-9704-75c908372eb9
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d33e055e9d73e786d822df2659bc490bc8646b9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-an-implicit-transaction-using-transaction-scope"></a>Implementowanie transakcji niejawnej przy użyciu zakresu transakcji
<xref:System.Transactions.TransactionScope> Klasa udostępnia w prosty sposób oznaczyć bloku kodu jako udział w transakcji, bez konieczności interakcji z transakcja. Zakres transakcji można wybrać i automatycznie zarządzać otoczenia transakcji. Ze względu na łatwość użycia i wydajności, zaleca się, że używasz <xref:System.Transactions.TransactionScope> klasy podczas opracowywania aplikacji transakcji.  
  
 Ponadto nie należy zarejestrować zasoby wyraźnie z transakcją. Wszelkie <xref:System.Transactions> Menedżera zasobów (takich jak SQL Server 2005) można wykryć istnienie otoczenia transakcji utworzone przez zakres i automatycznie zarejestrować.  
  
## <a name="creating-a-transaction-scope"></a>Tworzenie zakresu transakcji  
 Poniższy przykład przedstawia użycie prostego <xref:System.Transactions.TransactionScope> klasy.  
  
 [!code-csharp[TransactionScope#1](../../../../samples/snippets/csharp/VS_Snippets_Remoting/TransactionScope/cs/ScopeWithSQL.cs#1)]
 [!code-vb[TransactionScope#1](../../../../samples/snippets/visualbasic/VS_Snippets_Remoting/TransactionScope/vb/ScopeWithSQL.vb#1)]  
  
 Transakcja została uruchomiona po utworzeniu nowego <xref:System.Transactions.TransactionScope> obiektu.  Jak pokazano w przykładzie kodu, zalecane jest utworzenie zakresów z **przy użyciu** instrukcji. **Przy użyciu** instrukcji jest dostępne zarówno w języku C# i Visual Basic i działa, takich jak **try... finally** bloku, aby upewnić się, że zakres jest prawidłowo usuwane.  
  
 Podczas tworzenia instancji <xref:System.Transactions.TransactionScope>, Menedżer transakcji określa, która transakcja wziąć udział w. Po określeniu zakresu zawsze uczestniczy w danej transakcji. Decyzja jest oparta na dwa składniki: Określa, czy transakcja otoczenia jest obecny i wartość **TransactionScopeOption** parametru w konstruktorze. Transakcja otoczenia jest transakcji, w którym wykonuje kodu. Odwołanie do transakcji otoczenia można uzyskać przez wywołanie metody statyczne klasy <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> właściwości <xref:System.Transactions.Transaction> klasy. Aby uzyskać więcej informacji o sposobie użycia tego parametru, zobacz [Zarządzanie przepływu transakcji przy użyciu TransactionScopeOption](#ManageTxFlow) tego tematu.  
  
## <a name="completing-a-transaction-scope"></a>Kończenie pracy zakresu transakcji  
 Gdy aplikacja wykonuje całą pracę chce wykonać w ramach transakcji, należy wywołać <xref:System.Transactions.TransactionScope.Complete%2A?displayProperty=nameWIthType> metody tylko raz do informowania menedżera transakcji jest można zatwierdzić transakcji. Jest bardzo dobrym rozwiązaniem, Umieść wywołanie <xref:System.Transactions.TransactionScope.Complete%2A> jako ostatnią instrukcją w **przy użyciu** bloku.  
  
 Nie można wywołać tej metody przerywa transakcji, ponieważ Menedżer transakcji interpretuje jako awarii systemu lub równoważne wyjątek w zakresie transakcji. Jednak wywołanie tej metody nie gwarantuje, że transakcji będzie zatwierdzone. Jest tylko sposób informowania menedżera transakcji Twój status. Po wywołaniu <xref:System.Transactions.TransactionScope.Complete%2A> metody jest już dostępne otoczenia transakcji przy użyciu <xref:System.Transactions.Transaction.Current%2A> właściwości i próby podjęły spowodują wyjątek.  
  
 Jeśli <xref:System.Transactions.TransactionScope> obiekt początkowo utworzony transakcji zatwierdzania transakcji przez Menedżera transakcji faktyczną pracę występuje po ostatnim wierszu kodu w **przy użyciu** bloku. Jeśli nie utworzył transakcji, zatwierdzanie występuje zawsze, gdy <xref:System.Transactions.CommittableTransaction.Commit%2A> jest wywoływana przez właściciela <xref:System.Transactions.CommittableTransaction> obiektu. W tym momencie Menedżera transakcji wywołuje zasobu menedżerów i informacją do zatwierdzania lub wycofywania na ich podstawie <xref:System.Transactions.TransactionScope.Complete%2A> na wywołano metodę <xref:System.Transactions.TransactionScope> obiektu.  
  
 **Przy użyciu** instrukcji upewnia się, że <xref:System.Transactions.TransactionScope.Dispose%2A> metody <xref:System.Transactions.TransactionScope> obiektu jest wywoływana, nawet jeśli wystąpi wyjątek. <xref:System.Transactions.TransactionScope.Dispose%2A> Metody oznacza koniec zakresu transakcji. Wyjątki, które mogą występować po wywołaniu tej metody nie może mieć wpływ na transakcji. Ta metoda również przywraca otoczenia transakcji jej poprzedniego stanu.  
  
 Element <xref:System.Transactions.TransactionAbortedException> jest generowany, jeśli zakres tworzy transakcji, a transakcja została przerwana. Element <xref:System.Transactions.TransactionInDoubtException> jest generowany, gdy Menedżer transakcji nie może podjąć decyzję zatwierdzania. Nie wyjątku, jeśli transakcja została zatwierdzona.  
  
## <a name="rolling-back-a-transaction"></a>Wycofywanie transakcji  
 Jeśli chcesz wycofać transakcji, nie należy wywołać <xref:System.Transactions.TransactionScope.Complete%2A> metody w zakresie transakcji. Na przykład może zgłosić wyjątek, w ramach zakresu. Transakcji, w których uczestniczy w zostaną wycofane.  
  
##  <a name="ManageTxFlow"></a>Zarządzanie za pomocą TransactionScopeOption przepływu transakcji  
 Mogą być zagnieżdżane zakresu transakcji przez wywołanie metody, która używa <xref:System.Transactions.TransactionScope> z wewnątrz metody, która używa własnego zakresu jako się w przypadku `RootMethod` w poniższym przykładzie metody  
  
```csharp  
void RootMethod()  
{  
     using(TransactionScope scope = new TransactionScope())  
     {  
          /* Perform transactional work here */  
          SomeMethod();  
          scope.Complete();  
     }  
}  
  
void SomeMethod()  
{  
     using(TransactionScope scope = new TransactionScope())  
     {  
          /* Perform transactional work here */  
          scope.Complete();  
     }  
}  
```  
  
 Zakres transakcji wierzchu nosi nazwę zakres głównego.  
  
 <xref:System.Transactions.TransactionScope> Udostępnia kilka przeciążenia konstruktorów, które akceptują wyliczenie typu <xref:System.Transactions.TransactionScopeOption>, definiujący transakcyjnych zachowanie zakresu.  
  
 Element <xref:System.Transactions.TransactionScope> obiekt zawiera trzy pozycje:  
  
-   Dołącz do otoczenia transakcji lub Utwórz nową, jeśli nie istnieje.  
  
-   Można nowego zakresu głównego, oznacza to, że uruchomić nowej transakcji i skonfigurować danej transakcji można nowej transakcji otoczenia w zakresie własnej.  
  
-   Nie w ogóle brać udział w transakcji. Z tego względu nie ma żadnej otoczenia transakcji.  
  
 Jeśli zakres jest utworzone za pomocą elementów <xref:System.Transactions.TransactionScopeOption.Required>i transakcja otoczenia jest obecna, zakres sprzężenia danej transakcji. Jeśli z drugiej strony, nie ma żadnej transakcji otoczenia, następnie zakres tworzy nową transakcję i stają się zakres głównego. Jest to wartość domyślna. Gdy <xref:System.Transactions.TransactionScopeOption.Required> jest używany, kod w zakresie nie jest konieczne działają inaczej, czy jest to główny lub po prostu dołączenie do otoczenia transakcji. Powinna ona działać tak samo w obu przypadkach.  
  
 Jeśli zakres jest utworzone za pomocą elementów <xref:System.Transactions.TransactionScopeOption.RequiresNew>, zawsze jest zakres głównego. Rozpoczyna się nowej transakcji, a jego transakcji staje się nowe otoczenia transakcji w zakresie.  
  
 Jeśli zakres jest utworzone za pomocą elementów <xref:System.Transactions.TransactionScopeOption.Suppress>, nigdy nie bierze udział w transakcji, niezależnie od tego, czy transakcja otoczenia jest obecny. Zakres, utworzono wystąpienie tej wartości zawsze mieć **null** jako jego transakcja otoczenia.  
  
 Powyższych opcji przedstawiono w poniższej tabeli.  
  
|TransactionScopeOption|Otoczenia transakcji|Zakres uczestniczy|  
|----------------------------|-------------------------|-----------------------------|  
|Wymagane|Nie|Nowa transakcja (będzie główny)|  
|Wymagane nowe|Nie|Nowa transakcja (będzie główny)|  
|Pomiń|Nie|Nie transakcji|  
|Wymagane|Tak|Otoczenia transakcji|  
|Wymagane nowe|Tak|Nowa transakcja (będzie główny)|  
|Pomiń|Tak|Nie transakcji|  
  
 Gdy <xref:System.Transactions.TransactionScope> obiektu sprzężenia istniejącej transakcji otoczenia, usuwania obiektu zakres nie może kończyć się transakcji, chyba że zakres przerywa transakcję. Jeśli otoczenia transakcji został utworzony przez zakres głównego, tylko wtedy, gdy zakres główny jest usunięty, nie <xref:System.Transactions.CommittableTransaction.Commit%2A> jest wywoływana w transakcji. Jeśli transakcja została utworzona ręcznie, zakończenia transakcji, gdy jest to zostało przerwane lub przydzielonej przez jej twórcę.  
  
 W poniższym przykładzie przedstawiono <xref:System.Transactions.TransactionScope> obiekt, który tworzy trzy obiekty zakresu zagnieżdżonych wszystkich wystąpień z innym <xref:System.Transactions.TransactionScopeOption> wartość.  
  
```csharp  
using(TransactionScope scope1 = new TransactionScope())   
//Default is Required   
{   
     using(TransactionScope scope2 = new   
      TransactionScope(TransactionScopeOption.Required))   
     {  
     ...  
     }   
  
     using(TransactionScope scope3 = new TransactionScope(TransactionScopeOption.RequiresNew))   
     {  
     ...  
     }   
  
     using(TransactionScope scope4 = new   
        TransactionScope(TransactionScopeOption.Suppress))   
    {  
     ...  
    }   
}  
```  
  
 W przykładzie pokazano blok kodu bez żadnych transakcja otoczenia Tworzenie nowego zakresu (`scope1`) z <xref:System.Transactions.TransactionScopeOption.Required>. Zakres `scope1` jest zakresem głównego, ponieważ tworzy nową transakcję (transakcji A) i sprawia, że transakcja A otoczenia transakcji. `Scope1`następnie tworzy trzy więcej obiektów, każdy z inną <xref:System.Transactions.TransactionScopeOption> wartość. Na przykład `scope2` jest tworzony z <xref:System.Transactions.TransactionScopeOption.Required>, a ponieważ istnieje transakcja otoczenia, dołączeniu pierwszego transakcji utworzony przez `scope1`. Należy pamiętać, że `scope3` zakres główny nowej transakcji, a `scope4` ma ma otoczenia transakcji.  
  
 Chociaż często używane wartości domyślne i większość <xref:System.Transactions.TransactionScopeOption> jest <xref:System.Transactions.TransactionScopeOption.Required>, inne wartości ma unikatowy z przeznaczeniem.  
  
 <xref:System.Transactions.TransactionScopeOption.Suppress>jest przydatne, gdy chcesz zachować operacji wykonywanych przez sekcję kodu, a nie chcesz przerwać otoczenia transakcji, jeśli operacje kończą się niepowodzeniem. Na przykład jeśli chcesz wykonywać rejestrowanie i Inspekcja operacji lub gdy chcesz opublikować zdarzenia subskrybentom niezależnie od tego czy transakcja otoczenia zatwierdza lub przerywa. Ta wartość umożliwia ma sekcji nietransakcyjnej kodu wewnątrz zakresu transakcji, jak pokazano w poniższym przykładzie.  
  
```csharp  
using(TransactionScope scope1 = new TransactionScope())  
{  
     try  
     {  
          //Start of non-transactional section   
          using(TransactionScope scope2 = new  
             TransactionScope(TransactionScopeOption.Suppress))  
          {  
               //Do non-transactional work here  
          }  
          //Restores ambient transaction here  
   }  
     catch  
     {}  
   //Rest of scope1  
}  
```  
  
### <a name="voting-inside-a-nested-scope"></a>Głosowanie wewnątrz zagnieżdżonej zakresu  
 Chociaż zagnieżdżony zakres może dołączyć do otoczenia transakcji zakresu głównego, wywoływania <xref:System.Transactions.TransactionScope.Complete%2A> w zakresie zagnieżdżone nie ma wpływu na zakres głównego. Tylko wtedy, gdy wszystkie zakresy z zakresu głównego do ostatni zakres zagnieżdżonych głosowania można zatwierdzić transakcji, będzie można zatwierdzić transakcji. Nie wywołuje metody <xref:System.Transactions.TransactionScope.Complete%2A> w zakresie zagnieżdżonych będzie miała wpływ na zakres głównego zgodnie z otoczenia transakcja zostanie natychmiast przerwane.  
  
## <a name="setting-the-transactionscope-timeout"></a>Ustawienie limitu czasu elementu TransactionScope  
 Niektóre z przeciążenia konstruktorów z <xref:System.Transactions.TransactionScope> akceptować wartości typu <xref:System.TimeSpan>, używany do sterowania limit czasu transakcji. Upłynął limit czasu ustawioną wartość zero oznacza nieskończony limit czasu. Nieskończony limit czasu przydaje się głównie na potrzeby debugowania, gdy chcesz wyizolować problem w logiki biznesowej przez krokowe wykonywanie kodu, a użytkownik nie chce transakcji, które można debugować limitu czasu podczas próby zlokalizowania problemu. Ostrożność bardzo przy użyciu wartości nieskończony limit czasu we wszystkich innych przypadkach, ponieważ zastępuje zabezpiecza przed zakleszczenia transakcji.  
  
 Zwykle ustawiana <xref:System.Transactions.TransactionScope> limitu czasu w celu wartości innej niż domyślny w obu przypadkach. Pierwsza to podczas tworzenia, gdy chcesz przetestować sposób dojść do wniosku przerwane transakcje. Przez ustawienie limitu czasu małej wartości (na przykład jeden milisekund), spowodować transakcji nie powiedzie się i w związku z tym można obserwować obsługę kodu błędu. Drugi przypadek, w którym można ustawić wartość jest mniejsza niż domyślna wartość limitu czasu jest, jeśli uważasz, że zakres polega konfliktu zasobów, co spowoduje zakleszczenia. W takim przypadku chcesz przerwać transakcji, jak najszybciej i nie czeka na domyślna wartość limitu czasu wygaśnięcia.  
  
 Gdy zakres sprzężenia otoczenia transakcji, ale określa limit czasu mniejsze niż ma ustawioną wartość transakcji otoczenia, nowe, krótszy limit czasu jest wymuszane na <xref:System.Transactions.TransactionScope> obiektu i zakres musi kończyć się w czasie zagnieżdżonych określonym lub transakcja jest automatycznie przerwana. Jeśli limit czasu zagnieżdżony zakres jest więcej niż otoczenia transakcji, ustawienie nie działa.  
  
## <a name="setting-the-transactionscope-isolation-level"></a>Ustawienie poziomu izolacji elementu TransactionScope  
 Niektóre z przeciążenia konstruktorów z <xref:System.Transactions.TransactionScope> zaakceptować struktury typu <xref:System.Transactions.TransactionOptions> określa poziom izolacji, oprócz wartość limitu czasu. Domyślnie transakcji wykonuje z ustawioną poziom izolacji <xref:System.Transactions.IsolationLevel.Serializable>. Wybranie innego niż poziom izolacji <xref:System.Transactions.IsolationLevel.Serializable> jest najczęściej używana w systemach intensywnie korzysta z odczytu. Wymaga to pełny opis przetwarzania interpretacją i semantyka transakcja współbieżności problemy związane z i skutków spójności systemu transakcji.  
  
 Ponadto nie wszystkie menedżerów zasobów obsługuje wszystkie poziomy izolacji i może zdecydować się do wzięcia udziału w transakcji na wyższym poziomie niż skonfigurowane.  
  
 Każdy poziom izolacji poza <xref:System.Transactions.IsolationLevel.Serializable> się niespójność wynikające z innych transakcji dostęp do tych samych informacji. Różnica między izolacji różne poziomy w ten sposób do odczytu i zapisu blokady są używane. Blokada może zostać pociągnięty tylko wtedy, gdy transakcji uzyskuje dostęp do danych w Menedżerze zasobów lub może zostać pociągnięty do momentu transakcji nie zostanie przekazana lub zostało przerwane. Jest lepsze przepustowości, ten ostatni w celu zachowania spójności. Dwa rodzaje blokady i dwa rodzaje operacji (odczyt/zapis) dostarcza cztery poziomy izolacji podstawowe. Aby uzyskać więcej informacji, zobacz <xref:System.Transactions.IsolationLevel>.  
  
 Po użyciu zagnieżdżone <xref:System.Transactions.TransactionScope> obiektów, wszystkie zakresy zagnieżdżonych musi być skonfigurowany do użycia dokładnie ten sam poziom izolacji, aby dołączyć otoczenia transakcji. Jeśli zagnieżdżonych <xref:System.Transactions.TransactionScope> obiektu próbuje dołączyć otoczenia transakcji, jeszcze określa poziom izolacji różnych <xref:System.ArgumentException> zgłaszany.  
  
## <a name="interop-with-com"></a>Usługę międzyoperacyjną z modelu COM +  
 Podczas tworzenia nowego <xref:System.Transactions.TransactionScope> wystąpienie, można użyć <xref:System.Transactions.EnterpriseServicesInteropOption> wyliczenia w jednym z konstruktorów do określenia sposobu interakcji z modelu COM +. Aby uzyskać więcej informacji o tym, zobacz [współdziałanie z usługami przedsiębiorstwa i transakcje COM +](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Transactions.Transaction.Clone%2A>  
 <xref:System.Transactions.TransactionScope>
