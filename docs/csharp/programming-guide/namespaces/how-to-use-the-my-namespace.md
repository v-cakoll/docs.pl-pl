---
title: 'Instrukcje: Użyj mojej Namespace - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 9621f6a01ef4e30bf34b97df3d2c3033e9b62a23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678702"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="97b8b-102">Instrukcje: Użyj mojej Namespace (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="97b8b-102">How to: Use the My Namespace (C# Programming Guide)</span></span>
<span data-ttu-id="97b8b-103"><xref:Microsoft.VisualBasic.MyServices> Przestrzeni nazw (`My` w języku Visual Basic) udostępnia proste i intuicyjne szereg klas .NET Framework, dzięki któremu można napisać kod, który wchodzi w interakcję z komputera, aplikacji, ustawień, zasobów i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="97b8b-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="97b8b-104">Mimo że początkowo przeznaczona dla języka Visual Basic `MyServices` przestrzeni nazw mogą być używane w aplikacji w języku C#.</span><span class="sxs-lookup"><span data-stu-id="97b8b-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="97b8b-105">Aby uzyskać więcej informacji o korzystaniu z `MyServices` obszaru nazw w języku Visual Basic, zobacz [tworzenie aplikacji przy użyciu mojego](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="97b8b-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="97b8b-106">Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="97b8b-106">Adding a Reference</span></span>  
 <span data-ttu-id="97b8b-107">Przed użyciem `MyServices` klas w Twoim rozwiązaniu, należy dodać odwołanie do biblioteki języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="97b8b-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="97b8b-108">Aby dodać odwołanie do biblioteki języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="97b8b-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="97b8b-109">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** , a następnie wybierz węzeł **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="97b8b-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="97b8b-110">Gdy **odwołania** pojawi się okno dialogowe, przewiń listę w dół i wybierz Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="97b8b-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="97b8b-111">Możesz również umieścić następujący wiersz w `using` sekcji przy uruchamianiu programu.</span><span class="sxs-lookup"><span data-stu-id="97b8b-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="97b8b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="97b8b-112">Example</span></span>  
 <span data-ttu-id="97b8b-113">Ten przykład wywołuje różnych metod statycznych zawarte w `MyServices` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="97b8b-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="97b8b-114">Dla tego kodu do kompilacji należy dodać odwołania do pliku Microsoft.VisualBasic.DLL w do projektu.</span><span class="sxs-lookup"><span data-stu-id="97b8b-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="97b8b-115">Nie wszystkie klasy w `MyServices` przestrzeni nazw mogą być wywoływane z aplikacji w języku C#: na przykład <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> klasy nie jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="97b8b-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="97b8b-116">W tym konkretnym przypadku metody statyczne, są częścią <xref:Microsoft.VisualBasic.FileIO.FileSystem>, które również znajdują się w VisualBasic.dll, można zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="97b8b-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="97b8b-117">Na przykład Oto jak duplikowanie katalogu za pomocą jedną z metod:</span><span class="sxs-lookup"><span data-stu-id="97b8b-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="97b8b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97b8b-118">See also</span></span>

- [<span data-ttu-id="97b8b-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="97b8b-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="97b8b-120">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="97b8b-120">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="97b8b-121">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="97b8b-121">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)
