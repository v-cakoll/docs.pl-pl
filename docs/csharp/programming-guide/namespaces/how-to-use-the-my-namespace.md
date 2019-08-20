---
title: 'Instrukcje: Użycie mojej przestrzeni nazw — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: ff00a60d92ec6abbeb257abec76ed2812867f651
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588866"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Instrukcje: Korzystanie z przestrzeni nazw myC# (Przewodnik programowania)
Przestrzeń nazw (`My` w Visual Basic) zapewnia łatwy i intuicyjny dostęp do kilku klas .NET Framework, dzięki czemu można napisać kod, który współdziała z komputerem, aplikacją, ustawieniami, zasobami i tak dalej. <xref:Microsoft.VisualBasic.MyServices> Chociaż pierwotnie zaprojektowane do użytku z Visual Basic, `MyServices` przestrzeń nazw może być używana w C# aplikacjach.  
  
 Aby uzyskać więcej informacji o używaniu `MyServices` przestrzeni nazw z Visual Basic, zobacz [Programowanie za pomocą My](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Dodawanie odwołania  
 Aby można było używać `MyServices` klas w rozwiązaniu, należy dodać odwołanie do biblioteki Visual Basic.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Aby dodać odwołanie do biblioteki Visual Basic  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** i wybierz polecenie **Dodaj odwołanie**.  
  
2. Gdy pojawi się okno dialogowe **odwołania** , przewiń w dół listy i wybierz pozycję Microsoft. VisualBasic. dll.  
  
     W `using` sekcji na początku programu może być również uwzględniona następująca linia.  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a>Przykład  
 Ten przykład wywołuje różne metody statyczne zawarte w `MyServices` przestrzeni nazw. Dla tego kodu do skompilowania do projektu należy dodać odwołanie do Microsoft. VisualBasic. DLL.  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 Nie wszystkie klasy w `MyServices` przestrzeni nazw mogą być wywoływane z C# aplikacji: <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> na przykład Klasa nie jest zgodna. W tym konkretnym przypadku zamiast tego można użyć metod statycznych, <xref:Microsoft.VisualBasic.FileIO.FileSystem>które są częścią, które są również zawarte w pliku VisualBasic. dll. Na przykład poniżej przedstawiono sposób korzystania z jednej z tych metod do duplikowania katalogu:  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Przestrzenie nazw](./index.md)
- [Używanie przestrzeni nazw](./using-namespaces.md)
