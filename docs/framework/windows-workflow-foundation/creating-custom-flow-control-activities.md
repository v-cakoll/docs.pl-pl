---
title: Tworzenie niestandardowych działań sterowania przepływem
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: 8e7d4caad197631509fe80a5b5a08eff4d228c1c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989730"
---
# <a name="creating-custom-flow-control-activities"></a>Tworzenie niestandardowych działań sterowania przepływem
.NET Framework zawiera różne działania związane z kontrolą przepływu, które działają podobnie do abstrakcyjnych struktur programowania (takich jak <xref:System.Activities.Statements.Flowchart>) lub do standardowych instrukcji programistycznych (takich <xref:System.Activities.Statements.If>jak). W tym temacie omówiono architekturę jednego z przykładowych projektów, [nieogólne foreach](./samples/non-generic-foreach.md).  
  
## <a name="creating-the-custom-class"></a>Tworzenie klasy niestandardowej  
 Ponieważ nieogólna Klasa foreach będzie musiała zaplanować działania podrzędne, musi pochodzić od <xref:System.Activities.NativeActivity>, ponieważ działania pochodzące z programu <xref:System.Workflow.Activities.CodeActivity> nie mają tej funkcji.  
  
```csharp  
public sealed class ForEach : NativeActivity  
{
}
```  
  
 Klasa niestandardowa wymaga kilku elementów członkowskich do przechowywania danych używanych przez działanie oraz zapewnia funkcjonalność do wykonywania działań podrzędnych działania. Te elementy członkowskie obejmują:  
  
- `valueEnumerator`: Niepubliczny <xref:System.Activities.Variable%601> typ <xref:System.Collections.IEnumerator> używany do iteracji w kolekcji elementów. Ten element członkowski jest typu <xref:System.Activities.Variable%601> , ponieważ jest używany wewnętrznie w działaniu, a nie jako argument lub właściwość publiczna, która będzie używana, jeśli ten obiekt miał miejsce pochodzenia poza działaniem.  
  
- `OnChildComplete`: Właściwość publiczna <xref:System.Activities.CompletionCallback> , która jest wykonywana po zakończeniu wykonywania każdego elementu podrzędnego. Ten element członkowski jest zdefiniowany jako właściwość CLR, ponieważ jego wartość nie zmieni się dla różnych wystąpień działania.  
  
- `Values`: Kolekcja wejść używanych dla iteracji działania podrzędnego. Ten element członkowski jest typu <xref:System.Activities.InArgument%601>, ponieważ źródło danych znajduje się poza działaniem, ale nie można zmienić zawartości kolekcji podczas wykonywania działania. Jeśli działanie wymagało zmiany zawartości tej kolekcji podczas wykonywania działania (w celu dodania lub usunięcia działań, na przykład), ten element członkowski zostałby zdefiniowany jako <xref:System.Activities.ActivityAction>, który następnie będzie oceniany za każdym razem uzyskano do niego dostęp, dzięki czemu zmiany byłyby dostępne dla działania.  
  
- `Body`: Ten element członkowski definiuje działanie, które ma zostać wykonane dla każdego elementu `Values` w kolekcji. Ten element członkowski jest zdefiniowany jako <xref:System.Activities.ActivityAction> , aby był oceniany za każdym razem, gdy jest on dostępny.  
  
- `Execute`: Ta metoda używa `InternalExecute`, i `OnForEachComplete` `GetStateAndExecute` niepublicznych składowych, aby zaplanować wykonywanie i przypisać procedurę obsługi uzupełniania dla działania podrzędnego zdefiniowanego w składowej treści.  
  
- `CacheMetadata`: Ten element członkowski udostępnia środowisko uruchomieniowe z informacjami wymaganymi do wykonania działania. Domyślnie `CacheMetadata` Metoda działania będzie informować środowisko uruchomieniowe wszystkich publicznych elementów członkowskich działania, ale ponieważ to działanie używa prywatnych elementów członkowskich dla niektórych funkcji, musi informować środowiska uruchomieniowego o ich istnieniu, aby można było poznać środowisko uruchomieniowe niego. W takim przypadku `CacheMetadata` funkcja jest zastępowana, aby można było uzyskać `valueEnumerator` dostęp do prywatnego elementu członkowskiego. Ten element członkowski tworzy również argument wartości dla działania, dzięki czemu można je przekazywać do działania podczas wykonywania.
