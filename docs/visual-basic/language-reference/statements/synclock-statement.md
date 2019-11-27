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
ms.openlocfilehash: 0f430edce99513b0de9ef437d70648a128b336b8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352819"
---
# <a name="synclock-statement"></a>SyncLock — Instrukcja
Uzyskuje blokadę na wyłączność dla bloku instrukcji przed wykonaniem bloku.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Części  
 `lockobject`  
 Wymagany. Wyrażenie, którego wynikiem jest odwołanie do obiektu.  
  
 `block`  
 Opcjonalny. Blok instrukcji, które mają zostać wykonane po pozyskaniu blokady.  
  
 `End SyncLock`  
 Kończy blok `SyncLock`.  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `SyncLock` zapewnia, że wiele wątków nie wykonuje w tym samym czasie bloku instrukcji. `SyncLock` uniemożliwia każdemu wątkowi przejście do bloku, dopóki nie zostanie on uruchomiony przez inny wątek.  
  
 Typowym zastosowaniem `SyncLock` jest ochrona danych przed aktualizacją przez więcej niż jeden wątek jednocześnie. Jeśli instrukcje dotyczące manipulowania danymi muszą przejść do zakończenia bez zakłóceń, umieścić je wewnątrz bloku `SyncLock`.  
  
 Blok instrukcji chroniony przez blokadę wyłączną jest czasami nazywany *sekcją krytyczną*.  
  
## <a name="rules"></a>Reguły  
  
- Rozgałęzianie. Nie można rozgałęzić do bloku `SyncLock` spoza bloku.  
  
- Wartość blokady obiektu. Nie można `Nothing`wartości `lockobject`. Należy utworzyć obiekt blokady przed użyciem go w instrukcji `SyncLock`.  
  
     Nie można zmienić wartości `lockobject` podczas wykonywania bloku `SyncLock`. Mechanizm wymaga, aby obiekt blokady pozostał niezmieniony.  
  
- Nie można użyć operatora [await](../../../visual-basic/language-reference/operators/await-operator.md) w bloku `SyncLock`.  
  
## <a name="behavior"></a>Zachowanie  
  
- Ustanawia. Gdy wątek osiągnie instrukcję `SyncLock`, oblicza wyrażenie `lockobject` i wstrzymuje wykonywanie do momentu uzyskania blokady na wyłączność obiektu zwróconego przez wyrażenie. Gdy inny wątek osiągnie instrukcję `SyncLock`, nie uzyskuje blokady do momentu wykonania instrukcji `End SyncLock` przez pierwszy wątek.  
  
- Chronione dane. Jeśli `lockobject` jest zmienną `Shared`, blokada wyłączna zapobiega wykonywaniu przez wątek w jakimkolwiek wystąpieniu klasy `SyncLock` bloku, gdy wykonuje inny wątek. Chroni to dane, które są współużytkowane przez wszystkie wystąpienia.  
  
     Jeśli `lockobject` jest zmienną wystąpienia (nie `Shared`), blokada uniemożliwia `SyncLock` wykonywanie wątku uruchomionego w bieżącym wystąpieniu w tym samym czasie co inny wątek w tym samym wystąpieniu. Zapewnia to ochronę danych przechowywanych przez poszczególne wystąpienia.  
  
- Pozyskiwanie i wydanie. Blok `SyncLock` zachowuje się jak konstrukcja `Try...Finally`, w której blok `Try` uzyskuje blokadę na wyłączność na `lockobject` i zwalnia ją przez blok `Finally`. W związku z tym blok `SyncLock` gwarantuje wydanie blokady bez względu na sposób zamykania bloku. Jest to prawdziwe nawet w przypadku nieobsłużonego wyjątku.  
  
- Wywołania struktury. Blok `SyncLock` uzyskuje i zwalnia blokadę wyłączną, wywołując metody `Enter` i `Exit` klasy `Monitor` w przestrzeni nazw <xref:System.Threading>.  
  
## <a name="programming-practices"></a>Praktyki programowania  
 Wyrażenie `lockobject` powinno zawsze być oceniane do obiektu, który należy wyłącznie do klasy. Należy zadeklarować zmienną obiektu `Private`, aby chronić dane należące do bieżącego wystąpienia, lub zmienną obiektu `Private Shared` do ochrony danych wspólnych dla wszystkich wystąpień.  
  
 Nie należy używać słowa kluczowego `Me`, aby zapewnić obiekt blokady dla danych wystąpienia. Jeśli kod zewnętrzny dla klasy ma odwołanie do wystąpienia klasy, może użyć tego odwołania jako obiektu blokady dla bloku `SyncLock` całkowicie innego niż ty, chroniąc różne dane. W ten sposób Klasa i inna Klasa mogą blokować wykonywanie ich niepowiązanych bloków `SyncLock`. Podobne blokowanie na ciągu może być problematyczne, ponieważ jakikolwiek inny kod w procesie, który używa tego samego ciągu, będzie współużytkować tę samą blokadę.  
  
 Nie należy również używać metody `Me.GetType`, aby zapewnić obiekt blokady dla danych udostępnionych. Jest to spowodowane tym, że `GetType` zawsze zwraca ten sam obiekt `Type` dla danej nazwy klasy. Kod zewnętrzny może wywoływać `GetType` w klasie i uzyskać ten sam obiekt blokady, którego używasz. Spowoduje to, że dwie klasy blokują siebie nawzajem z ich bloków `SyncLock`.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia klasę, która utrzymuje prostą listę komunikatów. Przechowuje komunikaty w tablicy i ostatni używany element tej tablicy w zmiennej. Procedura `addAnotherMessage` zwiększa ostatni element i zapisuje nowy komunikat. Te dwie operacje są chronione przez instrukcje `SyncLock` i `End SyncLock`, ponieważ po zwiększeniu ostatniego elementu nowy komunikat musi być przechowywany przed ponownym zwiększeniem ostatniego elementu.  
  
 Jeśli Klasa `simpleMessageList` udostępnia jedną listę komunikatów między wszystkimi wystąpieniami, zmienne `messagesList` i `messagesLast` byłyby zadeklarowane jako `Shared`. W takim przypadku zmienna `messagesLock` powinna być również `Shared`, dzięki czemu będzie on miał pojedynczy obiekt blokady używany przez każde wystąpienie.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie są wykorzystywane wątki i `SyncLock`. Tak długo, jak jest obecna instrukcja `SyncLock`, blok instrukcji jest sekcją krytyczną, a `balance` nigdy nie będzie liczbą ujemną. Można skomentować instrukcje `SyncLock` i `End SyncLock`, aby zobaczyć efekt opuszczania słowa kluczowego `SyncLock`.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>Komentarze  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Przegląd elementów podstawowych synchronizacji](../../../standard/threading/overview-of-synchronization-primitives.md)
