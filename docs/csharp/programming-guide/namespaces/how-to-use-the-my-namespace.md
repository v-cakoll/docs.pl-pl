---
title: Jak korzystać z obszaru nazw My - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 063b46a32ced859c6c86e40c4a6b9870c3decd24
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700422"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Jak korzystać z obszaru moje jamien (Przewodnik programowania C#)
Obszar <xref:Microsoft.VisualBasic.MyServices> nazw`My` (w języku Visual Basic) zapewnia łatwy i intuicyjny dostęp do wielu klas .NET Framework, umożliwiając pisanie kodu, który współdziała z komputerem, aplikacją, ustawieniami, zasobami i tak dalej. Mimo że pierwotnie przeznaczone do użytku `MyServices` z języka Visual Basic, obszar nazw może służyć w aplikacjach Języka C#.  
  
 Aby uzyskać więcej `MyServices` informacji na temat korzystania z obszaru nazw z języka Visual Basic, zobacz [Programopracowywanie z moim](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Dodawanie odwołania  
 Przed użyciem `MyServices` klas w rozwiązaniu należy dodać odwołanie do biblioteki języka Visual Basic.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Aby dodać odwołanie do biblioteki języka Visual Basic  
  
1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Odwołania** i wybierz polecenie **Dodaj odwołanie**.  
  
2. Po **wyświetleniu** okna dialogowego Odwołania przewiń listę w dół i wybierz pozycję Microsoft.VisualBasic.dll.  
  
     Można również dołączyć następujący wiersz w `using` sekcji na początku programu.  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wywołuje różne metody `MyServices` statyczne zawarte w przestrzeni nazw. Aby ten kod został skompilowany, należy dodać odwołanie do pliku Microsoft.VisualBasic.DLL do projektu.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 Nie wszystkie klasy `MyServices` w przestrzeni nazw można wywołać z aplikacji <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> C#: na przykład klasa nie jest zgodna. W tym konkretnym przypadku można użyć metod <xref:Microsoft.VisualBasic.FileIO.FileSystem>statycznych, które są częścią , które są również zawarte w VisualBasic.dll, można użyć zamiast tego. Na przykład oto jak użyć jednej takiej metody do duplikowania katalogu:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Przestrzenie nazw](./index.md)
- [Używanie przestrzeni nazw](./using-namespaces.md)
