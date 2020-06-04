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
ms.openlocfilehash: fd932a20af274faf2b56136a94675b28399989b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404164"
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
 Kończy `SyncLock` blok.  
  
## <a name="remarks"></a>Uwagi  
 `SyncLock`Instrukcja zapewnia, że wiele wątków nie wykonuje w tym samym czasie bloku instrukcji. `SyncLock`zapobiega wprowadzaniu bloku przez każdy wątek do momentu wykonania innego wątku.  
  
 Najbardziej typowym zastosowaniem `SyncLock` jest ochrona danych przed aktualizacją przez więcej niż jeden wątek jednocześnie. Jeśli instrukcje dotyczące manipulowania danymi muszą przejść do zakończenia bez zakłóceń, umieścić je wewnątrz `SyncLock` bloku.  
  
 Blok instrukcji chroniony przez blokadę wyłączną jest czasami nazywany *sekcją krytyczną*.  
  
## <a name="rules"></a>Reguły  
  
- Rozgałęzianie. Nie można rozgałęzić `SyncLock` bloku spoza bloku.  
  
- Wartość blokady obiektu. Wartość `lockobject` nie może być `Nothing` . Należy utworzyć obiekt blokady przed użyciem go w `SyncLock` instrukcji.  
  
     Nie można zmienić wartości `lockobject` podczas wykonywania `SyncLock` bloku. Mechanizm wymaga, aby obiekt blokady pozostał niezmieniony.  
  
- Nie można użyć operatora [await](../operators/await-operator.md) w `SyncLock` bloku.  
  
## <a name="behavior"></a>Zachowanie  
  
- Ustanawia. Gdy wątek osiągnie `SyncLock` instrukcję, oblicza `lockobject` wyrażenie i wstrzymuje wykonywanie do momentu uzyskania blokady na wyłączność obiektu zwróconego przez wyrażenie. Gdy inny wątek osiągnie `SyncLock` instrukcję, nie uzyskuje blokady do momentu wykonania instrukcji przez pierwszy wątek `End SyncLock` .  
  
- Chronione dane. Jeśli `lockobject` jest `Shared` zmienną, blokada wyłączna uniemożliwia wątek w dowolnym wystąpieniu klasy z wykonywania `SyncLock` bloku, gdy wykonuje inny wątek. Chroni to dane, które są współużytkowane przez wszystkie wystąpienia.  
  
     Jeśli `lockobject` jest zmienną wystąpienia (nie `Shared` ), blokada uniemożliwia wykonywanie przez wątek w bieżącym wystąpieniu `SyncLock` bloku w tym samym czasie co inny wątek w tym samym wystąpieniu. Zapewnia to ochronę danych przechowywanych przez poszczególne wystąpienia.  
  
- Pozyskiwanie i wydanie. `SyncLock`Blok zachowuje się jak konstrukcja, `Try...Finally` w której `Try` blok uzyskuje blokadę na wyłączność `lockobject` i `Finally` blokuje ją. W związku z tym `SyncLock` blok gwarantuje wydanie blokady bez względu na sposób zamykania bloku. Jest to prawdziwe nawet w przypadku nieobsłużonego wyjątku.  
  
- Wywołania struktury. `SyncLock`Blok uzyskuje i zwalnia blokadę na wyłączność, wywołując `Enter` `Exit` metody i `Monitor` klasy w <xref:System.Threading> przestrzeni nazw.  
  
## <a name="programming-practices"></a>Praktyki programowania  
 `lockobject`Wyrażenie powinno zawsze być oceniane do obiektu, który należy wyłącznie do klasy. Należy zadeklarować `Private` zmienną obiektu, aby chronić dane należące do bieżącego wystąpienia, lub `Private Shared` zmienną obiektu, aby chronić dane wspólne dla wszystkich wystąpień.  
  
 Nie należy używać `Me` słowa kluczowego, aby dostarczyć obiekt blokady dla danych wystąpienia. Jeśli kod zewnętrzny dla klasy zawiera odwołanie do wystąpienia klasy, może użyć tego odwołania jako obiektu blokady dla `SyncLock` bloku całkowicie innego niż ty, chroniąc różne dane. W ten sposób Klasa i inna Klasa mogą blokować wykonywanie ich niepowiązanych `SyncLock` bloków. Podobne blokowanie na ciągu może być problematyczne, ponieważ jakikolwiek inny kod w procesie, który używa tego samego ciągu, będzie współużytkować tę samą blokadę.  
  
 Nie należy również używać metody, `Me.GetType` Aby zapewnić obiekt blokady dla danych udostępnionych. Jest to spowodowane tym `GetType` , że zawsze zwraca ten sam `Type` obiekt dla danej nazwy klasy. Kod zewnętrzny może wywoływać `GetType` w klasie i uzyskać ten sam obiekt blokady, którego używasz. Spowoduje to, że dwie klasy blokują siebie nawzajem z ich `SyncLock` bloków.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia klasę, która utrzymuje prostą listę komunikatów. Przechowuje komunikaty w tablicy i ostatni używany element tej tablicy w zmiennej. `addAnotherMessage`Procedura zwiększa ostatni element i zapisuje nowy komunikat. Te dwie operacje są chronione przez `SyncLock` instrukcje i `End SyncLock` , ponieważ po zwiększeniu ostatniego elementu nowy komunikat musi być przechowywany przed ponownym zwiększeniem ostatniego elementu.  
  
 Jeśli `simpleMessageList` Klasa udostępnia jedną listę komunikatów między wszystkimi wystąpieniami, zmienne `messagesList` i `messagesLast` byłyby zadeklarowane jako `Shared` . W takim przypadku zmienna `messagesLock` powinna również być `Shared` , tak aby istniał pojedynczy obiekt blokady używany przez każde wystąpienie.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie zastosowano wątki i `SyncLock` . Tak długo, jak `SyncLock` jest obecna instrukcja, blok instrukcji jest sekcją krytyczną i `balance` nigdy nie jest liczbą ujemną. Można dodać komentarz `SyncLock` `End SyncLock` do instrukcji i, aby zobaczyć efekt opuszczenia `SyncLock` słowa kluczowego.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>Komentarze  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Przegląd elementów podstawowych synchronizacji](../../../standard/threading/overview-of-synchronization-primitives.md)
