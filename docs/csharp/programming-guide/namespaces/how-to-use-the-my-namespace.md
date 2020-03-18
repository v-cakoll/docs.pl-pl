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
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="0101e-102">Jak korzystać z obszaru moje jamien (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="0101e-102">How to use the My namespace (C# Programming Guide)</span></span>
<span data-ttu-id="0101e-103">Obszar <xref:Microsoft.VisualBasic.MyServices> nazw`My` (w języku Visual Basic) zapewnia łatwy i intuicyjny dostęp do wielu klas .NET Framework, umożliwiając pisanie kodu, który współdziała z komputerem, aplikacją, ustawieniami, zasobami i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="0101e-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="0101e-104">Mimo że pierwotnie przeznaczone do użytku `MyServices` z języka Visual Basic, obszar nazw może służyć w aplikacjach Języka C#.</span><span class="sxs-lookup"><span data-stu-id="0101e-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="0101e-105">Aby uzyskać więcej `MyServices` informacji na temat korzystania z obszaru nazw z języka Visual Basic, zobacz [Programopracowywanie z moim](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="0101e-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="0101e-106">Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="0101e-106">Adding a Reference</span></span>  
 <span data-ttu-id="0101e-107">Przed użyciem `MyServices` klas w rozwiązaniu należy dodać odwołanie do biblioteki języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0101e-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="0101e-108">Aby dodać odwołanie do biblioteki języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0101e-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="0101e-109">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Odwołania** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="0101e-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="0101e-110">Po **wyświetleniu** okna dialogowego Odwołania przewiń listę w dół i wybierz pozycję Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="0101e-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="0101e-111">Można również dołączyć następujący wiersz w `using` sekcji na początku programu.</span><span class="sxs-lookup"><span data-stu-id="0101e-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="0101e-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="0101e-112">Example</span></span>  
 <span data-ttu-id="0101e-113">W tym przykładzie wywołuje różne metody `MyServices` statyczne zawarte w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0101e-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="0101e-114">Aby ten kod został skompilowany, należy dodać odwołanie do pliku Microsoft.VisualBasic.DLL do projektu.</span><span class="sxs-lookup"><span data-stu-id="0101e-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="0101e-115">Nie wszystkie klasy `MyServices` w przestrzeni nazw można wywołać z aplikacji <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> C#: na przykład klasa nie jest zgodna.</span><span class="sxs-lookup"><span data-stu-id="0101e-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="0101e-116">W tym konkretnym przypadku można użyć metod <xref:Microsoft.VisualBasic.FileIO.FileSystem>statycznych, które są częścią , które są również zawarte w VisualBasic.dll, można użyć zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="0101e-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="0101e-117">Na przykład oto jak użyć jednej takiej metody do duplikowania katalogu:</span><span class="sxs-lookup"><span data-stu-id="0101e-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="0101e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0101e-118">See also</span></span>

- [<span data-ttu-id="0101e-119">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="0101e-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0101e-120">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="0101e-120">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="0101e-121">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="0101e-121">Using Namespaces</span></span>](./using-namespaces.md)
