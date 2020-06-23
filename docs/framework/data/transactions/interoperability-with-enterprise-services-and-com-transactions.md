---
title: Współdziałanie z usługami przedsiębiorstwa i transakcjami COM+
description: Informacje o współdziałaniu z usługami przedsiębiorstwa i transakcjami modelu COM+ w programie .NET przy użyciu przestrzeni nazw System. Transactions.
ms.date: 03/30/2017
ms.assetid: d0fd0d26-fe86-443b-b208-4d57d39fa4aa
ms.openlocfilehash: ebd6166fbd99ef102cf10ba1bcef9e3eb8aaa5da
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141904"
---
# <a name="interoperability-with-enterprise-services-and-com-transactions"></a>Współdziałanie z usługami przedsiębiorstwa i transakcjami COM+
<xref:System.Transactions> Przestrzeń nazw obsługuje współdziałanie obiektów transakcji utworzone za pomocą tej przestrzeni nazw i transakcje utworzone za pomocą modelu COM +.  
  
 Można użyć <xref:System.Transactions.EnterpriseServicesInteropOption> wyliczenia podczas tworzenia nowego <xref:System.Transactions.TransactionScope> wystąpienie można określić poziom współpracy z modelu COM +.  
  
 Domyślnie, gdy kod aplikacji sprawdza Właściwość statyczną <xref:System.Transactions.Transaction.Current%2A> , program <xref:System.Transactions> próbuje wyszukać transakcję, która jest inna niż bieżąca, lub <xref:System.Transactions.TransactionScope> obiekt, który wskazuje, że <xref:System.Transactions.Transaction.Current%2A> jest **wartością null**. Jeśli dowolny z tych opcji, nie można odnaleźć <xref:System.Transactions> kwerendę kontekstu COM + dla transakcji. Należy pamiętać, że chociaż <xref:System.Transactions> może się okazać transakcji z modelu COM + kontekstu, transakcje, które są natywne go nadal preferuje <xref:System.Transactions>.  
  
## <a name="interoperability-levels"></a>Poziomy współpracy  
 <xref:System.Transactions.EnterpriseServicesInteropOption> Wyliczenie definiuje następujące poziomy współpracy —<xref:System.Transactions.EnterpriseServicesInteropOption.None>, <xref:System.Transactions.EnterpriseServicesInteropOption.Full> i <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>.  
  
 <xref:System.Transactions.TransactionScope> Udostępnia konstruktorów, które akceptują <xref:System.Transactions.EnterpriseServicesInteropOption> jako parametr.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.None>, jak nazywa się, oznacza, że nie ma współpracy między <xref:System.EnterpriseServices> kontekstami i zakresami transakcji. Po utworzeniu <xref:System.Transactions.TransactionScope> wraz z <xref:System.Transactions.EnterpriseServicesInteropOption.None>, zmiany wprowadzone w <xref:System.Transactions.Transaction.Current%2A> nie zostaną uwzględnione w kontekście COM +. Na tej samej zasadzie zmiany transakcji w kontekście COM + nie są zostaną uwzględnione w <xref:System.Transactions.Transaction.Current%2A>. Jest to najszybszy tryb działania dla <xref:System.Transactions> ponieważ nie istnieje żadne dodatkowe synchronizacji wymagane. <xref:System.Transactions.EnterpriseServicesInteropOption.None>jest wartością domyślną używaną przez <xref:System.Transactions.TransactionScope> Wszystkie konstruktory, które nie akceptują <xref:System.Transactions.EnterpriseServicesInteropOption> jako parametr.  
  
 Jeśli chcesz połączyć <xref:System.EnterpriseServices> transakcji z transakcją otoczenia, musisz użyć dowolnego <xref:System.Transactions.EnterpriseServicesInteropOption.Full> lub <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>. Obie te wartości wykorzystano funkcję usług bez składniki, a zatem powinno być uruchomione w dodatku Service Pack 2 dla systemu Windows XP lub Windows Server 2003 podczas korzystania z nich.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Full>Określa, że transakcje otoczenia <xref:System.Transactions> i <xref:System.EnterpriseServices> zawsze są takie same. Powoduje to utworzenie nowego <xref:System.EnterpriseServices> kontekstu transakcyjnego i zastosowanie transakcji, która jest aktualna dla <xref:System.Transactions.TransactionScope> bieżącego kontekstu. W związku z tym transakcja w programie <xref:System.Transactions.Transaction.Current%2A> jest w pełni zsynchronizowana z transakcją w programie <xref:System.EnterpriseServices.ContextUtil.Transaction%2A> . Ta wartość wprowadzono zmniejszenie wydajności, ponieważ może być konieczne do utworzenia nowego modelu COM + kontekstów.  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>określa następujące wymagania:  
  
- Gdy <xref:System.Transactions.Transaction.Current%2A> jest zaznaczone, <xref:System.Transactions> powinien obsługiwać transakcji w kontekście COM +, jeśli wykryje, że jest uruchomiona w kontekście innej niż domyślny kontekst. Należy zauważyć, że domyślnego kontekstu nie może zawierać transakcję. Dlatego w domyślnym kontekście, nawet w przypadku <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, transakcji przechowywane w magazynie lokalnym wątek używany przez <xref:System.Transactions> jest zwracana dla <xref:System.Transactions.Transaction.Current%2A>.  
  
- Jeśli nowy <xref:System.Transactions.TransactionScope> obiekt zostanie utworzony i tworzenie występuje w kontekście innej niż domyślny kontekst transakcji dla bieżącego <xref:System.Transactions.TransactionScope> obiekt powinien być zostaną uwzględnione w modelu COM +. W takim przypadku <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> zachowuje się jak <xref:System.Transactions.EnterpriseServicesInteropOption.Full> w tym tworzy nowy kontekst COM +.  
  
 Ponadto, gdy <xref:System.Transactions.Transaction.Current%2A> jest ustawiony w obu <xref:System.Transactions.EnterpriseServicesInteropOption.Full> i <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> , oba te tryby implikują, że <xref:System.Transactions.Transaction.Current%2A> nie można ustawić bezpośrednio.  Dowolne próba ustawienia <xref:System.Transactions.Transaction.Current%2A> bezpośrednio w innych niż tworzenie <xref:System.Transactions.TransactionScope> powoduje <xref:System.InvalidOperationException>. <xref:System.Transactions.EnterpriseServicesInteropOption>Wartość wyliczenia jest dziedziczona przez nowe zakresy transakcji, które nie określają jawnie wartości, która ma zostać użyta. Na przykład, jeśli tworzysz nowy <xref:System.Transactions.TransactionScope> obiekt za pomocą <xref:System.Transactions.EnterpriseServicesInteropOption.Full> , a następnie utworzysz drugi obiekt, <xref:System.Transactions.TransactionScope> ale nie określisz <xref:System.Transactions.EnterpriseServicesInteropOption> wartości, drugi <xref:System.Transactions.TransactionScope> obiekt również ma <xref:System.Transactions.EnterpriseServicesInteropOption.Full> .  
  
 Podsumowując, podczas tworzenia nowego zakresu transakcji są stosowane następujące reguły:  
  
1. <xref:System.Transactions.Transaction.Current%2A>jest sprawdzenie, czy jest transakcję. Tego wyboru powoduje:  
  
    - Sprawdź, czy jest zakresem.  
  
    - Jeśli wartość z zakresu <xref:System.Transactions.EnterpriseServicesInteropOption> zaznaczono wyliczenia przekazany w czasie zakresu.  
  
    - Jeśli <xref:System.Transactions.EnterpriseServicesInteropOption> ma ustawioną wartość wyliczenia <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>, transakcji COM + (<xref:System.EnterpriseServices> transakcji) pierwszeństwo <xref:System.Transactions> transakcji w lokalnego magazynu zarządzanych wątków.  
  
         Jeśli wartość jest równa <xref:System.Transactions.EnterpriseServicesInteropOption.None>, <xref:System.Transactions> transakcji w lokalnego magazynu wątków zarządzanych pierwszeństwo.  
  
         Jeśli wartość jest <xref:System.Transactions.EnterpriseServicesInteropOption.Full>, istnieje tylko jeden transakcji i jest transakcji COM +.  
  
2. Wartość <xref:System.Transactions.TransactionScopeOption> wyliczenia przekazany <xref:System.Transactions.TransactionScope> zaznaczono konstruktora. Określa, czy należy utworzyć nową transakcję.  
  
3. Jeśli nowa transakcja jest do utworzenia następujące wartości <xref:System.Transactions.EnterpriseServicesInteropOption> za:  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.Full>: utworzono transakcję skojarzoną z kontekstem COM+.  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.None>: <xref:System.Transactions> transakcja została utworzona.  
  
    - <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>: Jeśli istnieje kontekst COM+, transakcja zostanie utworzona i dołączona do kontekstu.  
  
 W poniższej tabeli przedstawiono kontekstu usługi Enterprise (ES) i transakcyjnych zakres, który wymaga transakcji przy użyciu <xref:System.Transactions.EnterpriseServicesInteropOption> wyliczenia.  
  
|Kontekst ES|Brak|Automatyczny|Pełne|  
|----------------|----------|---------------|----------|  
|Domyślny kontekst|Domyślny kontekst|Domyślny kontekst|Tworzenie nowego elementu <br />kontekst transakcji|  
|Inne niż domyślny kontekst|Obsługa kontekst klienta|Tworzy nowy kontekst transakcji|Tworzy nowy kontekst transakcji|  
  
 W poniższej tabeli przedstawiono co otoczenia transakcja jest, biorąc pod uwagę określonego <xref:System.EnterpriseServices> kontekstu i transakcyjnych zakres, który wymaga transakcji przy użyciu <xref:System.Transactions.EnterpriseServicesInteropOption> wyliczenia.  
  
|Kontekst ES|Brak|Automatyczny|Pełne|  
|----------------|----------|---------------|----------|  
|Domyślny kontekst|SKLEP|SKLEP|ES|  
|Inne niż domyślny kontekst|SKLEP|ES|ES|  
  
 W powyższej tabeli:  
  
- ST oznacza, że zakres transakcji otoczenia jest zarządzane przez <xref:System.Transactions>, niezależne od dowolnego <xref:System.EnterpriseServices> w kontekście transakcji, które mogą być obecne.  
  
- ES oznacza, że zakres otoczenia transakcja jest taka sama jak <xref:System.EnterpriseServices> w kontekście transakcji.
