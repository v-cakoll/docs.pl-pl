---
title: SyncLock — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: 5a931199ff8d09412d536a173f3cd12e451def64
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2018
ms.locfileid: "48845983"
---
# <a name="synclock-statement"></a>SyncLock — Instrukcja
Uzyskuje blokady na wyłączność dla bloku instrukcji, przed wykonaniem tego bloku.  
  
## <a name="syntax"></a>Składnia  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Części  
 `lockobject`  
 Wymagane. Wyrażenie, którego wynikiem jest odwołanie do obiektu.  
  
 `block`  
 Opcjonalna. Blok instrukcji, które są do wykonania, gdy jest blokada.  
  
 `End SyncLock`  
 Kończy blok `SyncLock`.  
  
## <a name="remarks"></a>Uwagi  
 `SyncLock` Instrukcji zapewnia, że wiele wątków nie wykonuje bloku instrukcji w tym samym czasie. `SyncLock` Każdy wątek uniemożliwia wprowadzanie bloku, dopóki go wykonuje nie innych wątków.  
  
 Najbardziej powszechnym zastosowaniem programu `SyncLock` jest ochrona danych przed jest aktualizowana przez więcej niż jeden wątek jednocześnie. Jeśli instrukcji, które manipulowania danymi muszą przejść do zakończenia bez przeszkód, umieść je wewnątrz `SyncLock` bloku.  
  
 Blok instrukcji, chronione przez blokady na wyłączność jest czasami nazywane *sekcję krytyczną*.  
  
## <a name="rules"></a>reguły  
  
-   Podręcznik rozgałęziania. Nie można rozgałęzić do `SyncLock` uniemożliwiaj poza blokiem.  
  
-   Wartość obiektu blokady. Wartość `lockobject` nie może być `Nothing`. Należy utworzyć obiekt blokady, zanim użyjesz go w `SyncLock` instrukcji.  
  
     Nie można zmienić wartość `lockobject` podczas wykonywania `SyncLock` bloku. Mechanizm wymaga, aby zablokować obiektu pozostają niezmienione.  
  
-   Nie można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w `SyncLock` bloku.  
  
## <a name="behavior"></a>Zachowanie  
  
-   Mechanizm. Gdy wątek osiągnie `SyncLock` instrukcji, ocenia `lockobject` wyrażenia i zawiesza wykonywanie, dopóki nie otrzymuje blokady na wyłączność w obiekcie zwracanym przez wyrażenie. Gdy inny wątek osiągnie `SyncLock` instrukcji, go nie uzyskania blokady do momentu pierwszego wątek `End SyncLock` instrukcji.  
  
-   Chronione dane. Jeśli `lockobject` jest `Shared` zmiennej blokady na wyłączność zapobiega wątku w żadnym wystąpieniu klasy wykonywania `SyncLock` blokowania podczas jego wykonywania innych wątków. Chroni to dane, które jest współużytkowana przez wszystkie wystąpienia.  
  
     Jeśli `lockobject` jest zmienną instance (nie `Shared`), Blokada zapobiega wątku działającego w ramach bieżącego wystąpienia wykonania `SyncLock` bloku, w tym samym czasie jako inny wątek w tym samym wystąpieniu. Chroni to danych obsługiwanych przez poszczególne wystąpienia.  
  
-   Pozyskiwanie i wersji. A `SyncLock` blok, który zachowuje się jak `Try...Finally` konstrukcji, w którym `Try` bloku uzyskuje blokady na wyłączność w `lockobject` i `Finally` bloku zwalnia go. W związku z tym `SyncLock` bloku gwarantuje wydanie lock, niezależnie od tego, jak zamknąć blok. Ta zasada obowiązuje nawet w przypadku nieobsługiwanego wyjątku.  
  
-   Struktura wywołuje. `SyncLock` Blok uzyskuje i zwalnia blokady na wyłączność przez wywołanie metody `Enter` i `Exit` metody `Monitor` klasy w <xref:System.Threading> przestrzeni nazw.  
  
## <a name="programming-practices"></a>Programowanie rozwiązań  
 `lockobject` Wyrażenia zawsze powinna być obiekt, który należy wyłącznie do swojej klasy. Należy zadeklarować `Private` zmiennej obiektu, aby chronić dane należące do bieżącego wystąpienia lub `Private Shared` zmiennej obiektu, aby chronić dane wspólne dla wszystkich wystąpień.  
  
 Nie należy używać `Me` — słowo kluczowe, aby zapewnić blokadę dla wystąpienia obiektu danych. Jeśli kod zewnętrzny klasy zawiera odwołanie do wystąpienia klasy, można użyć tego odwołania jako obiekt blokady dla `SyncLock` bloku zupełnie inne niż należy do Ciebie, ochrony danych. W ten sposób klasy i inne klasy może zablokować wzajemnie wykonanie ich niepowiązanych `SyncLock` bloków. Podobnie blokowania na ciąg może być problematyczne, ponieważ każdy inny kod proces, korzystając z tych samych parametrach współużytkują ten sam blokady.  
  
 Ponadto nie należy korzystać z `Me.GetType` metody w celu zapewnienia obiektu blokady dla udostępnionych danych. Jest to spowodowane `GetType` zawsze zwraca wartość taka sama `Type` obiektu dla nazwy danej klasy. Można wywołać kod zewnętrzny `GetType` na klasie i uzyskania tego samego obiektu blokady są używane. Spowodowałoby to dwie klasy blokuje wzajemnie z ich `SyncLock` bloków.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia klasę zawierającą prostą listę komunikatów. Przechowuje komunikaty w tablicy, a ostatnio używany element tablicy w zmiennej. `addAnotherMessage` Procedury zwiększa ostatni element i zapisuje nowy komunikat. Te dwie operacje są chronione przez `SyncLock` i `End SyncLock` instrukcji, ponieważ po ostatnim elemencie została zwiększona, Nowa wiadomość musi być przechowywany przed innych wątków można zwiększyć po ostatnim elemencie ponownie.  
  
 Jeśli `simpleMessageList` klasy udostępnione jedną listę komunikatów między wszystkie jego wystąpienia, zmienne `messagesList` i `messagesLast` może być zadeklarowana jako `Shared`. W tym przypadku zmienna `messagesLock` powinny być `Shared`, dzięki czemu będzie obiektem pojedynczego blokady używany przez każde wystąpienie.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie użyto wątków i `SyncLock`. Tak długo, jak `SyncLock` instrukcji, blok instrukcji to sekcja krytycznego i `balance` nigdy nie stanie się liczbą ujemną. Możesz przekształcić w komentarz `SyncLock` i `End SyncLock` instrukcje, aby zobaczyć efekt pomijając `SyncLock` — słowo kluczowe.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a>Komentarze  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Przegląd elementów podstawowych synchronizacji](../../../standard/threading/overview-of-synchronization-primitives.md)
