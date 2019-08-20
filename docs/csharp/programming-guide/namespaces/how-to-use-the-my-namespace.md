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
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="702af-102">Instrukcje: Korzystanie z przestrzeni nazw myC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="702af-102">How to: Use the My Namespace (C# Programming Guide)</span></span>
<span data-ttu-id="702af-103">Przestrzeń nazw (`My` w Visual Basic) zapewnia łatwy i intuicyjny dostęp do kilku klas .NET Framework, dzięki czemu można napisać kod, który współdziała z komputerem, aplikacją, ustawieniami, zasobami i tak dalej. <xref:Microsoft.VisualBasic.MyServices></span><span class="sxs-lookup"><span data-stu-id="702af-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="702af-104">Chociaż pierwotnie zaprojektowane do użytku z Visual Basic, `MyServices` przestrzeń nazw może być używana w C# aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="702af-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="702af-105">Aby uzyskać więcej informacji o używaniu `MyServices` przestrzeni nazw z Visual Basic, zobacz [Programowanie za pomocą My](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="702af-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="702af-106">Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="702af-106">Adding a Reference</span></span>  
 <span data-ttu-id="702af-107">Aby można było używać `MyServices` klas w rozwiązaniu, należy dodać odwołanie do biblioteki Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="702af-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="702af-108">Aby dodać odwołanie do biblioteki Visual Basic</span><span class="sxs-lookup"><span data-stu-id="702af-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="702af-109">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="702af-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="702af-110">Gdy pojawi się okno dialogowe **odwołania** , przewiń w dół listy i wybierz pozycję Microsoft. VisualBasic. dll.</span><span class="sxs-lookup"><span data-stu-id="702af-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="702af-111">W `using` sekcji na początku programu może być również uwzględniona następująca linia.</span><span class="sxs-lookup"><span data-stu-id="702af-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="702af-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="702af-112">Example</span></span>  
 <span data-ttu-id="702af-113">Ten przykład wywołuje różne metody statyczne zawarte w `MyServices` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="702af-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="702af-114">Dla tego kodu do skompilowania do projektu należy dodać odwołanie do Microsoft. VisualBasic. DLL.</span><span class="sxs-lookup"><span data-stu-id="702af-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="702af-115">Nie wszystkie klasy w `MyServices` przestrzeni nazw mogą być wywoływane z C# aplikacji: <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> na przykład Klasa nie jest zgodna.</span><span class="sxs-lookup"><span data-stu-id="702af-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="702af-116">W tym konkretnym przypadku zamiast tego można użyć metod statycznych, <xref:Microsoft.VisualBasic.FileIO.FileSystem>które są częścią, które są również zawarte w pliku VisualBasic. dll.</span><span class="sxs-lookup"><span data-stu-id="702af-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="702af-117">Na przykład poniżej przedstawiono sposób korzystania z jednej z tych metod do duplikowania katalogu:</span><span class="sxs-lookup"><span data-stu-id="702af-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="702af-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="702af-118">See also</span></span>

- [<span data-ttu-id="702af-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="702af-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="702af-120">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="702af-120">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="702af-121">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="702af-121">Using Namespaces</span></span>](./using-namespaces.md)
