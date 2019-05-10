---
title: Tworzenie niestandardowych działań sterowania przepływem
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: f457e6f8cefd7183ca20cb449adf1ac15d7bde79
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647149"
---
# <a name="creating-custom-flow-control-activities"></a>Tworzenie niestandardowych działań sterowania przepływem
.NET Framework zawiera szereg działań przepływu sterowania, które działają podobnie do abstrakcyjnej struktur programowania (takich jak <xref:System.Activities.Statements.Flowchart>) lub standardowy instrukcji programowania (takich jak <xref:System.Activities.Statements.If>). W tym temacie omówiono architekturę jednego z przykładowych projektów, [ForEach Nieuniwersalne](./samples/non-generic-foreach.md).  
  
## <a name="creating-the-custom-class"></a>Tworzenie niestandardowej klasy  
 Ponieważ klasa ForEach Nieuniwersalne należy zaplanować działania podrzędne, trzeba będzie ją dziedziczyć <xref:System.Activities.NativeActivity>, od działań, które wynikają z <xref:System.Workflow.Activities.CodeActivity> nie korzystać z tej funkcji.  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 Klasa niestandardowa wymaga kilku członków do przechowywania danych używane przez działanie i umożliwiają korzystanie z funkcji do wykonania działania podrzędne działania. Te elementy członkowskie obejmują:  
  
- `valueEnumerator`: Bez publicznego <xref:System.Activities.Variable%601> typu <xref:System.Collections.IEnumerator> używana do iteracji w kolekcji elementów. Ten element jest typu <xref:System.Activities.Variable%601> , ponieważ jest używana wewnętrznie w działania, a nie argument lub właściwości publicznej, która będzie używana, gdyby zostały pochodzi spoza działania tego obiektu.  
  
- `OnChildComplete`: Publicznie <xref:System.Activities.CompletionCallback> właściwość, która wykonuje podczas każdego elementu podrzędnego kończy wykonywanie. Ten element członkowski jest zdefiniowany jako właściwość CLR, ponieważ różne wystąpienia działanie nie ulegnie zmianie jego wartość.  
  
- `Values`: Kolekcja używana dla iteracji działanie podrzędne w danych wejściowych. Ten element jest typu <xref:System.Activities.InArgument%601>, ponieważ źródło danych znajduje się poza działania, ale zawartość kolekcji nie powinna się zmieniać podczas wykonywania działania. W razie potrzeby działanie funkcji, aby zmienić zawartość tej kolekcji, podczas wykonywania działania (w celu dodania lub usunięcia działania, na przykład), ten element członkowski będzie zostały zdefiniowane jako <xref:System.Activities.ActivityAction>, który następnie może być ocenione każdym razem, gdy jego została otwarta, tak aby zmiany będą dostępne do działania.  
  
- `Body`: Ten element definiuje działania do wykonania dla każdego elementu w `Values` kolekcji. Ta składowa jest zdefiniowana jako <xref:System.Activities.ActivityAction> tak, że zostanie ono ocenione za każdym razem, gdy jest on dostępny.  
  
- `Execute`: Ta metoda używa `InternalExecute`, `OnForEachComplete`, i `GetStateAndExecute` elementów członkowskich niepublicznych, aby zaplanować wykonywanie i przypisać procedury obsługi zakończenia działania podrzędnego, zdefiniowane w elemencie członkowskim treści.  
  
- `CacheMetadata`: Ten element członkowski udostępnia środowisko uruchomieniowe informacje potrzebne do wykonania działania. Domyślnie działania firmy `CacheMetadata` metodę poinformuje środowiska uruchomieniowego wszystkie publiczne elementy członkowskie działania, ale ponieważ to działanie używane prywatnych elementów członkowskich dla niektórych funkcji, należy go poinformowania środowiska wykonawczego o ich istnieniu aby środowisko uruchomieniowe może mieć świadomość je. W tym przypadku `CacheMetadata` funkcji zostanie zastąpiona, aby prywatna `valueEnumerator` elementu członkowskiego jest możliwy. Ten element członkowski tworzy również argument dla wartości dla działania, aby ich mogą być przekazane do działania podczas wykonywania.
