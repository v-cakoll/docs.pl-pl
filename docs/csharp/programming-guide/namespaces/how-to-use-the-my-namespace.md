---
title: Jak korzystać z przewodnika po C# programowaniu przestrzeni nazw
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 063b46a32ced859c6c86e40c4a6b9870c3decd24
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75700422"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Jak używać przestrzeni nazw my (C# Przewodnik programowania)
Przestrzeń nazw <xref:Microsoft.VisualBasic.MyServices> (`My` w Visual Basic) zapewnia łatwy i intuicyjny dostęp do kilku klas .NET Framework, umożliwiając pisanie kodu, który współdziała z komputerem, aplikacją, ustawieniami, zasobami itd. Mimo że pierwotnie zaprojektowane do użycia z Visual Basic, `MyServices` przestrzeni nazw można używać w C# aplikacjach.  
  
 Aby uzyskać więcej informacji o używaniu przestrzeni nazw `MyServices` z Visual Basic, zobacz [Programowanie za pomocą My](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Dodawanie odwołania  
 Aby można było używać klas `MyServices` w rozwiązaniu, należy dodać odwołanie do biblioteki Visual Basic.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Aby dodać odwołanie do biblioteki Visual Basic  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** i wybierz polecenie **Dodaj odwołanie**.  
  
2. Gdy pojawi się okno dialogowe **odwołania** , przewiń w dół listy i wybierz pozycję Microsoft. VisualBasic. dll.  
  
     Można również umieścić następujący wiersz w sekcji `using` na początku programu.  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Przykład  
 Ten przykład wywołuje różne metody statyczne zawarte w przestrzeni nazw `MyServices`. Dla tego kodu do skompilowania do projektu należy dodać odwołanie do Microsoft. VisualBasic. DLL.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 Nie wszystkie klasy w przestrzeni nazw `MyServices` mogą być wywoływane z C# aplikacji: na przykład Klasa <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> nie jest zgodna. W tym konkretnym przypadku zamiast tego można użyć metod statycznych, które są częścią <xref:Microsoft.VisualBasic.FileIO.FileSystem>, które są również zawarte w pliku VisualBasic. dll. Na przykład poniżej przedstawiono sposób korzystania z jednej z tych metod do duplikowania katalogu:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Przestrzenie nazw](./index.md)
- [Używanie przestrzeni nazw](./using-namespaces.md)
