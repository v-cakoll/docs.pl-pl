---
title: Jak użyć słownika zasobów zakresu aplikacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 5bfb3ed0304598a5acf4b7682bf4a4169c5153d1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459797"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="35940-102">Jak użyć słownika zasobów zakresu aplikacji</span><span class="sxs-lookup"><span data-stu-id="35940-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="35940-103">Ten przykład przedstawia sposób definiowania i używania niestandardowego słownika zasobów zakresu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35940-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35940-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="35940-104">Example</span></span>  
 <span data-ttu-id="35940-105"><xref:System.Windows.Application> uwidacznia magazyn zakresu aplikacji dla zasobów udostępnionych: <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="35940-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="35940-106">Domyślnie właściwość <xref:System.Windows.Application.Resources%2A> jest inicjowana przy użyciu wystąpienia typu <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="35940-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="35940-107">To wystąpienie jest używane podczas pobierania i ustawiania właściwości zakresu aplikacji przy użyciu <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="35940-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="35940-108">Aby uzyskać więcej informacji, zobacz [jak: pobieranie i Ustawianie zasobu zakresu aplikacji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="35940-108">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="35940-109">Jeśli masz wiele zasobów ustawionych przy użyciu <xref:System.Windows.Application.Resources%2A>, zamiast tego możesz użyć niestandardowego słownika zasobów do przechowywania tych zasobów i ustawić w zamian <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="35940-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="35940-110">Poniżej przedstawiono sposób deklarowania niestandardowego słownika zasobów przy użyciu języka XAML.</span><span class="sxs-lookup"><span data-stu-id="35940-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="35940-111">Wymiana całych słowników zasobów przy użyciu <xref:System.Windows.Application.Resources%2A> umożliwia obsługę motywów zakresu aplikacji, gdzie każdy motyw jest hermetyzowany przez pojedynczy słownik zasobów.</span><span class="sxs-lookup"><span data-stu-id="35940-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="35940-112">Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="35940-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="35940-113">Poniżej przedstawiono sposób pobierania zasobów zakresu aplikacji z słownika zasobów udostępnianych przez <xref:System.Windows.Application.Resources%2A> w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="35940-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="35940-114">Poniżej pokazano, jak można także uzyskać zasoby w kodzie.</span><span class="sxs-lookup"><span data-stu-id="35940-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="35940-115">Istnieją dwa kwestie, które należy wziąć pod uwagę podczas korzystania z <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="35940-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="35940-116">Najpierw *klucz* słownika jest obiektem, dlatego należy użyć dokładnie tego samego wystąpienia obiektu, gdy oba ustawienia i pobierają wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="35940-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="35940-117">(Należy pamiętać, że podczas korzystania z ciągu w kluczu jest rozróżniana wielkość liter). Po drugie, *wartość* słownika jest obiektem, dlatego konieczne będzie przekonwertowanie wartości na żądany typ podczas pobierania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="35940-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35940-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35940-118">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="35940-119">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="35940-119">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="35940-120">Połączone słowniki zasobów</span><span class="sxs-lookup"><span data-stu-id="35940-120">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
