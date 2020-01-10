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
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="d6e08-102">Jak używać przestrzeni nazw my (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="d6e08-102">How to use the My namespace (C# Programming Guide)</span></span>
<span data-ttu-id="d6e08-103">Przestrzeń nazw <xref:Microsoft.VisualBasic.MyServices> (`My` w Visual Basic) zapewnia łatwy i intuicyjny dostęp do kilku klas .NET Framework, umożliwiając pisanie kodu, który współdziała z komputerem, aplikacją, ustawieniami, zasobami itd.</span><span class="sxs-lookup"><span data-stu-id="d6e08-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="d6e08-104">Mimo że pierwotnie zaprojektowane do użycia z Visual Basic, `MyServices` przestrzeni nazw można używać w C# aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="d6e08-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="d6e08-105">Aby uzyskać więcej informacji o używaniu przestrzeni nazw `MyServices` z Visual Basic, zobacz [Programowanie za pomocą My](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="d6e08-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="d6e08-106">Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="d6e08-106">Adding a Reference</span></span>  
 <span data-ttu-id="d6e08-107">Aby można było używać klas `MyServices` w rozwiązaniu, należy dodać odwołanie do biblioteki Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d6e08-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="d6e08-108">Aby dodać odwołanie do biblioteki Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6e08-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="d6e08-109">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="d6e08-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="d6e08-110">Gdy pojawi się okno dialogowe **odwołania** , przewiń w dół listy i wybierz pozycję Microsoft. VisualBasic. dll.</span><span class="sxs-lookup"><span data-stu-id="d6e08-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="d6e08-111">Można również umieścić następujący wiersz w sekcji `using` na początku programu.</span><span class="sxs-lookup"><span data-stu-id="d6e08-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="d6e08-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6e08-112">Example</span></span>  
 <span data-ttu-id="d6e08-113">Ten przykład wywołuje różne metody statyczne zawarte w przestrzeni nazw `MyServices`.</span><span class="sxs-lookup"><span data-stu-id="d6e08-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="d6e08-114">Dla tego kodu do skompilowania do projektu należy dodać odwołanie do Microsoft. VisualBasic. DLL.</span><span class="sxs-lookup"><span data-stu-id="d6e08-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="d6e08-115">Nie wszystkie klasy w przestrzeni nazw `MyServices` mogą być wywoływane z C# aplikacji: na przykład Klasa <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> nie jest zgodna.</span><span class="sxs-lookup"><span data-stu-id="d6e08-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="d6e08-116">W tym konkretnym przypadku zamiast tego można użyć metod statycznych, które są częścią <xref:Microsoft.VisualBasic.FileIO.FileSystem>, które są również zawarte w pliku VisualBasic. dll.</span><span class="sxs-lookup"><span data-stu-id="d6e08-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="d6e08-117">Na przykład poniżej przedstawiono sposób korzystania z jednej z tych metod do duplikowania katalogu:</span><span class="sxs-lookup"><span data-stu-id="d6e08-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="d6e08-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6e08-118">See also</span></span>

- [<span data-ttu-id="d6e08-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d6e08-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d6e08-120">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="d6e08-120">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="d6e08-121">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="d6e08-121">Using Namespaces</span></span>](./using-namespaces.md)
