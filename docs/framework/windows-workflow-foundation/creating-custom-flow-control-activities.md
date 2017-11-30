---
title: "Tworzenie niestandardowego przepływu sterowania działań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 12b5c8db096c0261041c29385b0ebe2e1569078c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="creating-custom-flow-control-activities"></a>Tworzenie niestandardowego przepływu sterowania działań
.Net Framework zawiera szereg działań przepływu sterowania, które działają podobnie abstrakcyjnej struktury programowania (takich jak <xref:System.Activities.Statements.Flowchart>) lub standardowy instrukcje programowania (takich jak <xref:System.Activities.Statements.If>). W tym temacie omówiono architekturę jednego z przykładowych projektów [ForEach Nieogólny](../../../docs/framework/windows-workflow-foundation/samples/non-generic-foreach.md).  
  
## <a name="creating-the-custom-class"></a>Tworzenie niestandardowej klasy  
 Ponieważ klasa ForEach inne niż ogólne należy zaplanować działania podrzędne, trzeba będzie dziedziczyć <xref:System.Activities.NativeActivity>, ponieważ działaniach pochodzących z <xref:System.Workflow.Activities.CodeActivity> nie korzystać z tej funkcji.  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 Klasy niestandardowej wymaga kilka elementów członkowskich do przechowywania danych używany przez działanie i zapewniać funkcje do wykonywania działań podrzędnych działania. Elementy te obejmują:  
  
-   `valueEnumerator`Niepublicznych <xref:System.Activities.Variable%601> typu <xref:System.Collections.IEnumerator> używanej do wykonywania iteracji w kolekcji elementów. Ten element jest typu <xref:System.Activities.Variable%601> , ponieważ jest używana wewnętrznie w działania, a nie argument lub właściwość publiczna, które mają być używane, jeśli ten obiekt mieć początek poza danym działaniem.  
  
-   `OnChildComplete`: Publicznego <xref:System.Activities.CompletionCallback> właściwość, która wykonuje podczas każdego elementu podrzędnego zakończeniem wykonywania. Ten element członkowski jest zdefiniowany jako właściwość CLR, ponieważ jej wartość nie zmieni się w różnych wystąpieniach działania.  
  
-   `Values`: Kolekcja dane wejściowe, używane do iteracji działania podrzędnego. Ten element jest typu <xref:System.Activities.InArgument%601>, ponieważ źródło danych jest poza danym działaniem, ale nie oczekiwano zawartości kolekcji można zmienić podczas wykonywania działania. W razie potrzeby działania funkcji, aby zmienić zawartość tej kolekcji, podczas wykonywania działania (w celu dodania lub usunięcia działania, na przykład) tego elementu członkowskiego czy zostały zdefiniowane jako <xref:System.Activities.ActivityAction>, który następnie może być ocenione zawsze został dostęp do niej, dzięki czemu zmiany będą dostępne do działania.  
  
-   `Body`: Ten element definiuje działanie do wykonania dla każdego elementu w `Values` kolekcji. Ten element członkowski jest zdefiniowany jako <xref:System.Activities.ActivityAction> tak, aby była ona sprawdzana za każdym razem, gdy jest on dostępny.  
  
-   `Execute`: Ta metoda używa `InternalExecute`, `OnForEachComplete`, i `GetStateAndExecute` niepubliczne elementy członkowskie, aby zaplanować wykonanie i przypisać obsługi ukończenie działania podrzędnego zdefiniowane w elemencie członkowskim treści.  
  
-   `CacheMetadata`: Ten element członkowski zapewnia środowisko uruchomieniowe informacje potrzebne do wykonania działania. Domyślnie działania w `CacheMetadata` metody poinformuje środowiska uruchomieniowego wszystkich publicznych elementów członkowskich działania, ale ponieważ tego działania używa prywatne elementy członkowskie dla niektórych funkcji, należy go poinformować środowiska wykonawczego o ich istnienia środowiska uruchomieniowego można mieć świadomość je. W takim przypadku `CacheMetadata` funkcja jest wyłączona, aby prywatna `valueEnumerator` można można uzyskać dostępu do elementu członkowskiego. Ten element członkowski tworzy również argument wartości dla działania, aby ich można przekazać do działania podczas wykonywania.
