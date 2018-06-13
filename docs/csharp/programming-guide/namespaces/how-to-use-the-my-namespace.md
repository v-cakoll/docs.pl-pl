---
title: 'Porady: użycie przestrzeni nazw typu My (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: ceab0dbb2ded070fc7de4f5a59d778be2a54f9cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332013"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Porady: użycie przestrzeni nazw typu My (Przewodnik programowania w języku C#)
<xref:Microsoft.VisualBasic.MyServices> Przestrzeni nazw (`My` w języku Visual Basic) udostępnia proste i intuicyjne szereg klas .NET Framework, dzięki któremu można napisać kod, który współdziała z komputera, aplikacji, ustawień, zasobów i tak dalej. Mimo że pierwotnie przeznaczony do użytku z programem Visual Basic `MyServices` przestrzeni nazw mogą być używane w aplikacji C#.  
  
 Aby uzyskać więcej informacji o korzystaniu z `MyServices` przestrzeni nazw z języka Visual Basic, zobacz [programowanie z mojej](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Dodawanie odwołania  
 Przed użyciem `MyServices` klas w rozwiązaniu, należy dodać odwołanie do biblioteki języka Visual Basic.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Aby dodać odwołanie do biblioteki języka Visual Basic  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** , a następnie wybierz węzeł **Dodaj odwołanie**.  
  
2.  Gdy **odwołania** zostanie wyświetlone okno dialogowe, przewiń listę w dół i wybierz pliku Microsoft.VisualBasic.dll.  
  
     Można także zawierać następujący wiersz w `using` sekcji podczas uruchamiania programu.  
  
     [!code-csharp[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wywołuje różnych metod statycznych zawartych w `MyServices` przestrzeni nazw. W przypadku ten kod, aby skompilować odwołanie do pliku Microsoft.VisualBasic.DLL należy dodać do projektu.  
  
 [!code-csharp[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]  
  
 Nie wszystkie klasy w `MyServices` przestrzeni nazw może zostać wywołana z aplikacji C#: na przykład <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> klasy nie jest zgodny. W tym przypadku metod statycznych które są częścią <xref:Microsoft.VisualBasic.FileIO.FileSystem>, które również znajdują się w VisualBasic.dll, w zamian można używać. Na przykład poniżej przedstawiono sposób zduplikowane katalogu przy użyciu jednego takiego metody:  
  
 [!code-csharp[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md)  
 [Używanie przestrzeni nazw](../../../csharp/programming-guide/namespaces/using-namespaces.md)
