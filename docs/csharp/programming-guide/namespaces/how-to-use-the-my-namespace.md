---
title: "Porady: użycie przestrzeni nazw typu My (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f3564c594a5fbb9bd05a956e5c12bbb173d2db51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="21963-102">Porady: użycie przestrzeni nazw typu My (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="21963-102">How to: Use the My Namespace (C# Programming Guide)</span></span>
<span data-ttu-id="21963-103"><xref:Microsoft.VisualBasic.MyServices> Przestrzeni nazw (`My` w języku Visual Basic) udostępnia proste i intuicyjne szereg klas .NET Framework, dzięki któremu można napisać kod, który współdziała z komputera, aplikacji, ustawień, zasobów i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="21963-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="21963-104">Mimo że pierwotnie przeznaczony do użytku z programem Visual Basic `MyServices` przestrzeni nazw mogą być używane w aplikacji C#.</span><span class="sxs-lookup"><span data-stu-id="21963-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="21963-105">Aby uzyskać więcej informacji o korzystaniu z `MyServices` przestrzeni nazw z języka Visual Basic, zobacz [programowanie z mojej](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="21963-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="21963-106">Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="21963-106">Adding a Reference</span></span>  
 <span data-ttu-id="21963-107">Przed użyciem `MyServices` klas w rozwiązaniu, należy dodać odwołanie do biblioteki języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="21963-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="21963-108">Aby dodać odwołanie do biblioteki języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21963-108">To add a reference to the Visual Basic library</span></span>  
  
1.  <span data-ttu-id="21963-109">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** , a następnie wybierz węzeł **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="21963-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="21963-110">Gdy **odwołania** zostanie wyświetlone okno dialogowe, przewiń listę w dół i wybierz pliku Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="21963-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="21963-111">Można także zawierać następujący wiersz w `using` sekcji podczas uruchamiania programu.</span><span class="sxs-lookup"><span data-stu-id="21963-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="21963-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="21963-112">Example</span></span>  
 <span data-ttu-id="21963-113">W tym przykładzie wywołuje różnych metod statycznych zawartych w `MyServices` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="21963-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="21963-114">W przypadku ten kod, aby skompilować odwołanie do pliku Microsoft.VisualBasic.DLL należy dodać do projektu.</span><span class="sxs-lookup"><span data-stu-id="21963-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]  
  
 <span data-ttu-id="21963-115">Nie wszystkie klasy w `MyServices` przestrzeni nazw może zostać wywołana z aplikacji C#: na przykład <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> klasy nie jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="21963-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="21963-116">W tym przypadku metod statycznych które są częścią <xref:Microsoft.VisualBasic.FileIO.FileSystem>, które również znajdują się w VisualBasic.dll, w zamian można używać.</span><span class="sxs-lookup"><span data-stu-id="21963-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="21963-117">Na przykład poniżej przedstawiono sposób zduplikowane katalogu przy użyciu jednego takiego metody:</span><span class="sxs-lookup"><span data-stu-id="21963-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="21963-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21963-118">See Also</span></span>  
 [<span data-ttu-id="21963-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="21963-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="21963-120">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="21963-120">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="21963-121">Używanie usługi przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="21963-121">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)
