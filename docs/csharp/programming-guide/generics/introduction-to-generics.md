---
title: Wprowadzenie do typów ogólnych (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: 892b6bfe5cf18bde91221bb8b2fa7ca7a2813870
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321249"
---
# <a name="introduction-to-generics-c-programming-guide"></a>Wprowadzenie do typów ogólnych (Przewodnik programowania w języku C#)
Ogólne klasy i metody łączyć możliwość ponownego wykorzystania, zabezpieczeń i wydajności w taki sposób, aby ich odpowiedniki nierodzajową nie. Typy ogólne są najczęściej używane przez kolekcje i metod, które działają na nich. Biblioteka klas programu .NET Framework w wersji 2.0 zapewnia nowy obszar nazw <xref:System.Collections.Generic>, który zawiera kilka nowych klas kolekcję na podstawie ogólnego. Zaleca się, że wszystkie aplikacje których docelowe .NET Framework 2.0 i późniejszego użycia nowej kolekcji ogólnych klasy zamiast starsze odpowiedników nierodzajową takich jak <xref:System.Collections.ArrayList>. Aby uzyskać więcej informacji, zobacz [typy ogólne w .NET](../../../standard/generics/index.md).  
  
 Oczywiście można również tworzyć niestandardowe typy ogólne i metody w celu zapewnienia własne uogólniony rozwiązania i wzorce projektowe, które są bezpieczne i wydajne. Poniższy przykład kodu pokazuje proste klasy ogólnej listy połączone dla celów demonstracyjnych. (W większości przypadków należy użyć <xref:System.Collections.Generic.List%601> klasy w bibliotece klas programu .NET Framework, zamiast tworzyć własne.) Parametr typu `T` jest używany w kilku lokalizacjach, gdzie konkretnego typu zazwyczaj będzie używać do określenia typ elementu przechowywane na liście. Jest on używany w następujący sposób:  
  
-   Typ parametru metody w `AddHead` metody.  
  
-   Jako typ zwracany `Data` właściwości w zagnieżdżonych `Node` klasy.  
  
-   Jako typ prywatnego elementu członkowskiego `data` klasy zagnieżdżonej.  
  
 Należy pamiętać, że T jest dostępny dla zagnieżdżone `Node` klasy. Gdy `GenericList<T>` zostanie uruchomiony z konkretnego typu, na przykład jako `GenericList<int>`, każde wystąpienie `T` zostanie zastąpiony `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 Poniższy przykład kodu pokazuje, jak kod klienta używa ogólnego `GenericList<T>` klasy w celu utworzenia listy liczb całkowitych. Po prostu zmieniając argument typu następujący kod można łatwo można zmodyfikować utworzyć listę ciągów lub dowolnego niestandardowego typu:  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy ogólne](../../../csharp/programming-guide/generics/index.md)
