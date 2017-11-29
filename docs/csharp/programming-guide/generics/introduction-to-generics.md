---
title: "Wprowadzenie do typów ogólnych (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ec4fe9cc9fe7bf868fcc8afe4dc4e4234241e352
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-generics-c-programming-guide"></a>Wprowadzenie do typów ogólnych (Przewodnik programowania w języku C#)
Ogólne klasy i metody łączyć możliwość ponownego wykorzystania, zabezpieczeń i wydajności w taki sposób, aby ich odpowiedniki nierodzajową nie. Typy ogólne są najczęściej używane przez kolekcje i metod, które działają na nich. Biblioteka klas programu .NET Framework w wersji 2.0 zapewnia nowy obszar nazw <xref:System.Collections.Generic>, który zawiera kilka nowych klas kolekcję na podstawie ogólnego. Zaleca się, że wszystkie aplikacje których docelowe [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 lub nowszy Użyj nowe klasy rodzajowej kolekcji zamiast starsze odpowiedników nierodzajową takiego jak <xref:System.Collections.ArrayList>. Aby uzyskać więcej informacji, zobacz [typy ogólne w bibliotece klas programu .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).  
  
 Oczywiście można również tworzyć niestandardowe typy ogólne i metody w celu zapewnienia własne uogólniony rozwiązania i wzorce projektowe, które są bezpieczne i wydajne. Poniższy przykład kodu pokazuje proste klasy ogólnej listy połączone dla celów demonstracyjnych. (W większości przypadków należy użyć <xref:System.Collections.Generic.List%601> klasy w bibliotece klas programu .NET Framework, zamiast tworzyć własne.) Parametr typu `T` jest używany w kilku lokalizacjach, gdzie konkretnego typu zazwyczaj będzie używać do określenia typ elementu przechowywane na liście. Jest on używany w następujący sposób:  
  
-   Typ parametru metody w `AddHead` metody.  
  
-   Zwracany typ metody publicznej `GetNext` i `Data` właściwości w zagnieżdżonych `Node` klasy.  
  
-   Jako typ danych prywatnego elementu członkowskiego klasy zagnieżdżonej.  
  
 Należy pamiętać, że T jest dostępny dla zagnieżdżone `Node` klasy. Gdy `GenericList<T>` zostanie uruchomiony z konkretnego typu, na przykład jako `GenericList<int>`, każde wystąpienie `T` zostanie zastąpiony `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 Poniższy przykład kodu pokazuje, jak kod klienta używa ogólnego `GenericList<T>` klasy w celu utworzenia listy liczb całkowitych. Po prostu zmieniając argument typu następujący kod można łatwo można zmodyfikować utworzyć listę ciągów lub dowolnego niestandardowego typu:  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy ogólne](../../../csharp/programming-guide/generics/index.md)
