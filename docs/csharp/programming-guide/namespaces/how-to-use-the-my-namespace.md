---
title: 'Instrukcje: Użyj mojej Namespace - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: b56a421dd7b34bf006e1e6609bbb8ecc5f56e0bf
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971263"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="749f8-102">Instrukcje: Użyj mojej Namespace (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="749f8-102">How to: Use the My Namespace (C# Programming Guide)</span></span>
<span data-ttu-id="749f8-103"><xref:Microsoft.VisualBasic.MyServices> Przestrzeni nazw (`My` w języku Visual Basic) udostępnia proste i intuicyjne szereg klas .NET Framework, dzięki któremu można napisać kod, który wchodzi w interakcję z komputera, aplikacji, ustawień, zasobów i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="749f8-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="749f8-104">Mimo że początkowo przeznaczona dla języka Visual Basic `MyServices` przestrzeni nazw mogą być używane w aplikacji w języku C#.</span><span class="sxs-lookup"><span data-stu-id="749f8-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="749f8-105">Aby uzyskać więcej informacji o korzystaniu z `MyServices` obszaru nazw w języku Visual Basic, zobacz [tworzenie aplikacji przy użyciu mojego](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="749f8-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="749f8-106">Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="749f8-106">Adding a Reference</span></span>  
 <span data-ttu-id="749f8-107">Przed użyciem `MyServices` klas w Twoim rozwiązaniu, należy dodać odwołanie do biblioteki języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="749f8-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="749f8-108">Aby dodać odwołanie do biblioteki języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="749f8-108">To add a reference to the Visual Basic library</span></span>  
  
1.  <span data-ttu-id="749f8-109">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** , a następnie wybierz węzeł **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="749f8-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="749f8-110">Gdy **odwołania** pojawi się okno dialogowe, przewiń listę w dół i wybierz Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="749f8-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="749f8-111">Możesz również umieścić następujący wiersz w `using` sekcji przy uruchamianiu programu.</span><span class="sxs-lookup"><span data-stu-id="749f8-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="749f8-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="749f8-112">Example</span></span>  
 <span data-ttu-id="749f8-113">Ten przykład wywołuje różnych metod statycznych zawarte w `MyServices` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="749f8-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="749f8-114">Dla tego kodu do kompilacji należy dodać odwołania do pliku Microsoft.VisualBasic.DLL w do projektu.</span><span class="sxs-lookup"><span data-stu-id="749f8-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="749f8-115">Nie wszystkie klasy w `MyServices` przestrzeni nazw mogą być wywoływane z aplikacji w języku C#: na przykład <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> klasy nie jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="749f8-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="749f8-116">W tym konkretnym przypadku metody statyczne, są częścią <xref:Microsoft.VisualBasic.FileIO.FileSystem>, które również znajdują się w VisualBasic.dll, można zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="749f8-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="749f8-117">Na przykład Oto jak duplikowanie katalogu za pomocą jedną z metod:</span><span class="sxs-lookup"><span data-stu-id="749f8-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="749f8-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="749f8-118">See also</span></span>

- [<span data-ttu-id="749f8-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="749f8-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="749f8-120">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="749f8-120">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="749f8-121">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="749f8-121">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)
