---
title: SyncLock — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: cf2aad9ec2ba67200d175fbcddfcb49afeac6efc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="synclock-statement"></a>SyncLock — Instrukcja
Uzyskuje wyłącznej blokady dla blok instrukcji, przed wykonaniem bloku.  
  
## <a name="syntax"></a>Składnia  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Części  
 `lockobject`  
 Wymagana. Wyrażenie obliczane do odwołania do obiektu.  
  
 `block`  
 Opcjonalna. Blok instrukcji, które są do wykonania, gdy są uzyskiwane blokady.  
  
 `End SyncLock`  
 Kończy blok `SyncLock`.  
  
## <a name="remarks"></a>Uwagi  
 `SyncLock` Instrukcji gwarantuje, że wiele wątków nie wykonuje bloku instrukcji w tym samym czasie. `SyncLock` Każdy wątek uniemożliwia wprowadzanie bloku, dopóki nie innego wątku jest jej wykonanie.  
  
 Najczęściej używane `SyncLock` ma chronić dane przed aktualizowana przez więcej niż jeden wątek jednocześnie. Jeśli instrukcji, które manipulowania danymi muszą przejść do ukończenia bez przeszkód, umieść je w `SyncLock` bloku.  
  
 Blok instrukcji chronione w trybie wyłączności jest czasami nazywany *sekcja krytyczna*.  
  
## <a name="rules"></a>Reguły  
  
-   Rozgałęzianie. Nie można rozgałęzić do `SyncLock` zablokować poza blokiem.  
  
-   Wartość obiektu blokady. Wartość `lockobject` nie może być `Nothing`. Należy utworzyć obiekt blokady przed użyciem go w `SyncLock` instrukcji.  
  
     Nie można zmienić wartości `lockobject` podczas wykonywania `SyncLock` bloku. Mechanizm wymaga, aby zablokować obiektu pozostają niezmienione.  
  
-   Nie można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w `SyncLock` bloku.  
  
## <a name="behavior"></a>Zachowanie  
  
-   Mechanizm. Gdy osiągnie wątku `SyncLock` instrukcji, ocenia `lockobject` wyrażenie i wstrzymuje wykonywanie do momentu otrzymuje wyłącznej blokady obiektu zwróconego przez wyrażenie. Gdy osiągnie inny wątek `SyncLock` instrukcji go nie uzyskania blokady dopóki wykonuje pierwszym wątkiem `End SyncLock` instrukcji.  
  
-   Chronionych danych. Jeśli `lockobject` jest `Shared` zmiennej, blokada na wyłączność uniemożliwia wątku w żadnym wystąpieniu klasy wykonywania `SyncLock` zablokowanie, gdy jest jej wykonanie innego wątku. Pozwala to chronić dane, które jest współdzielona przez wszystkie wystąpienia.  
  
     Jeśli `lockobject` jest zmienna wystąpienia (nie `Shared`), blokada uniemożliwia uruchomiony w bieżącym wystąpieniu wykonywanie wątku `SyncLock` bloku, w tym samym czasie jako inny wątek w tym samym wystąpieniu. Jest to zabezpieczenie danych obsługiwanych przez poszczególne wystąpienia.  
  
-   Nabycia i wersji. A `SyncLock` bloku zachowuje się jak `Try...Finally` konstrukcji, w którym `Try` bloku uzyskuje w trybie wyłączności na `lockobject` i `Finally` zwolnieniem bloku. W związku z tym `SyncLock` bloku gwarantuje wersji blokady, niezależnie od tego, jak zakończyć bloku. Dotyczy to nawet w przypadku nieobsługiwany wyjątek.  
  
-   Wywołania Framework. `SyncLock` Blok uzyskuje i zwalnia blokada na wyłączność przez wywołanie metody `Enter` i `Exit` metody `Monitor` klasy w <xref:System.Threading> przestrzeni nazw.  
  
## <a name="programming-practices"></a>Rozwiązania w zakresie programowania  
 `lockobject` Wyrażenia zawsze powinna być obiekt, który należy wyłącznie do swojej klasy. Powinien deklarować `Private` zmienna obiektu do ochrony danych należących do bieżącego wystąpienia lub `Private Shared` zmienna obiektu, aby chronić dane wspólne dla wszystkich wystąpień.  
  
 Nie należy używać `Me` — słowo kluczowe w celu zapewnienia blokady dla wystąpienia obiektu danych. Jeśli kod zewnętrzny klasy zawiera odwołanie do wystąpienia klasy, można użyć tego odwołania dla obiekt blokady `SyncLock` bloku całkowicie różni się od należy do Ciebie, ochrony danych. W ten sposób, klasy i inne klasy można zablokować wzajemnie wykonywanie ich niepowiązanych `SyncLock` bloków. Podobnie blokowania na ciąg może sprawiać problemy, ponieważ innego kodu w procesie przy użyciu tych samych parametrach współużytkują tego samego blokady.  
  
 Ponadto nie należy korzystać z `Me.GetType` metodę w celu zapewnienia obiektu blokady dla udostępnionych danych. Jest to spowodowane `GetType` zawsze zwraca takie same `Type` obiektu dla nazwy danej klasy. Kod zewnętrzny można wywołać `GetType` w klasie i uzyskać ten sam obiekt blokady używasz. Spowodowałoby to dwie klasy blokuje siebie z ich `SyncLock` bloków.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia klasę zawierającą prostą listę komunikatów. Przechowuje komunikaty w tablicy i ostatniego używany element tablicy w zmiennej. `addAnotherMessage` Procedury zwiększa ostatnim elementem i przechowuje nowy komunikat. Tych dwóch operacji są chronione przez `SyncLock` i `End SyncLock` instrukcji, ponieważ po ostatnim elemencie została zwiększona, nowej wiadomości musi być przechowywany przed innego wątku może zwiększyć ostatni element ponownie.  
  
 Jeśli `simpleMessageList` klasy udostępnionych jedną listę komunikatów między wszystkie jego wystąpienia, zmienne `messagesList` i `messagesLast` może być zadeklarowana jako `Shared`. W tym przypadku zmiennej `messagesLock` należy również `Shared`, dzięki czemu będzie obiektu jedną blokadą używane przez każde wystąpienie.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie użyto wątków i `SyncLock`. Tak długo, jak `SyncLock` instrukcji, blok instrukcji jest sekcja krytyczna i `balance` nigdy nie jest liczbą ujemną. Możesz przekształcić w komentarz `SyncLock` i `End SyncLock` instrukcje, aby zobaczyć efekt pomijając `SyncLock` — słowo kluczowe.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a>Komentarze  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [Synchronizacja wątku](../../programming-guide/concepts/threading/thread-synchronization.md)  
 [Wątkowość](../../programming-guide/concepts/threading/index.md)
