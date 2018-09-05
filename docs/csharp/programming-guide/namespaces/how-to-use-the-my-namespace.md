---
title: 'Porady: użycie przestrzeni nazw typu My (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: a8ec3a96534693142d37d26ac0c08eec9298b178
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526209"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Porady: użycie przestrzeni nazw typu My (Przewodnik programowania w języku C#)
<xref:Microsoft.VisualBasic.MyServices> Przestrzeni nazw (`My` w języku Visual Basic) udostępnia proste i intuicyjne szereg klas .NET Framework, dzięki któremu można napisać kod, który wchodzi w interakcję z komputera, aplikacji, ustawień, zasobów i tak dalej. Mimo że początkowo przeznaczona dla języka Visual Basic `MyServices` przestrzeni nazw mogą być używane w aplikacji w języku C#.  
  
 Aby uzyskać więcej informacji o korzystaniu z `MyServices` obszaru nazw w języku Visual Basic, zobacz [tworzenie aplikacji przy użyciu mojego](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Dodawanie odwołania  
 Przed użyciem `MyServices` klas w Twoim rozwiązaniu, należy dodać odwołanie do biblioteki języka Visual Basic.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Aby dodać odwołanie do biblioteki języka Visual Basic  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** , a następnie wybierz węzeł **Dodaj odwołanie**.  
  
2.  Gdy **odwołania** pojawi się okno dialogowe, przewiń listę w dół i wybierz Microsoft.VisualBasic.dll.  
  
     Możesz również umieścić następujący wiersz w `using` sekcji przy uruchamianiu programu.  
  
     [!code-csharp[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]  
  
## <a name="example"></a>Przykład  
 Ten przykład wywołuje różnych metod statycznych zawarte w `MyServices` przestrzeni nazw. Dla tego kodu do kompilacji należy dodać odwołania do pliku Microsoft.VisualBasic.DLL w do projektu.  
  
 [!code-csharp[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]  
  
 Nie wszystkie klasy w `MyServices` przestrzeni nazw mogą być wywoływane z aplikacji w języku C#: na przykład <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> klasy nie jest zgodny. W tym konkretnym przypadku metody statyczne, są częścią <xref:Microsoft.VisualBasic.FileIO.FileSystem>, które również znajdują się w VisualBasic.dll, można zamiast tego. Na przykład Oto jak duplikowanie katalogu za pomocą jedną z metod:  
  
 [!code-csharp[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)  
- [Używanie przestrzeni nazw](../../../csharp/programming-guide/namespaces/using-namespaces.md)
