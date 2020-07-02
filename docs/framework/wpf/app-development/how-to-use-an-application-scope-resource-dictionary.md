---
title: Jak użyć słownika zasobów zakresu aplikacji
description: Dowiedz się, jak definiować i używać niestandardowego słownika zasobów zakresu aplikacji w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 9d117dea6c554339b4b462b9bf37b80da2dc477f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613712"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="ffe77-103">Jak użyć słownika zasobów zakresu aplikacji</span><span class="sxs-lookup"><span data-stu-id="ffe77-103">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="ffe77-104">Ten przykład przedstawia sposób definiowania i używania niestandardowego słownika zasobów zakresu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ffe77-104">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffe77-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ffe77-105">Example</span></span>  
 <span data-ttu-id="ffe77-106"><xref:System.Windows.Application>uwidacznia magazyn zakresu aplikacji dla zasobów udostępnionych: <xref:System.Windows.Application.Resources%2A> .</span><span class="sxs-lookup"><span data-stu-id="ffe77-106"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="ffe77-107">Domyślnie <xref:System.Windows.Application.Resources%2A> Właściwość jest inicjowana przy użyciu wystąpienia <xref:System.Windows.ResourceDictionary> typu.</span><span class="sxs-lookup"><span data-stu-id="ffe77-107">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="ffe77-108">To wystąpienie jest używane podczas pobierania i ustawiania właściwości zakresu aplikacji przy użyciu <xref:System.Windows.Application.Resources%2A> .</span><span class="sxs-lookup"><span data-stu-id="ffe77-108">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="ffe77-109">Aby uzyskać więcej informacji, zobacz [jak: pobieranie i Ustawianie zasobu zakresu aplikacji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ffe77-109">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="ffe77-110">Jeśli masz wiele zasobów ustawionych przy użyciu programu <xref:System.Windows.Application.Resources%2A> , możesz zamiast tego użyć niestandardowego słownika zasobów do przechowywania tych zasobów i ustawić <xref:System.Windows.Application.Resources%2A> je w zamian.</span><span class="sxs-lookup"><span data-stu-id="ffe77-110">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="ffe77-111">Poniżej przedstawiono sposób deklarowania niestandardowego słownika zasobów przy użyciu języka XAML.</span><span class="sxs-lookup"><span data-stu-id="ffe77-111">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="ffe77-112">Wymiana całych słowników zasobów przy użyciu programu <xref:System.Windows.Application.Resources%2A> umożliwia obsługę motywów zakresu aplikacji, gdzie każdy motyw jest hermetyzowany przez pojedynczy słownik zasobów.</span><span class="sxs-lookup"><span data-stu-id="ffe77-112">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="ffe77-113">Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.ResourceDictionary> .</span><span class="sxs-lookup"><span data-stu-id="ffe77-113">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="ffe77-114">Poniżej przedstawiono sposób pobierania zasobów zakresu aplikacji z słownika zasobów uwidocznionych <xref:System.Windows.Application.Resources%2A> w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="ffe77-114">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="ffe77-115">Poniżej pokazano, jak można także uzyskać zasoby w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ffe77-115">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="ffe77-116">Istnieją dwa kwestie, które należy wziąć pod uwagę podczas korzystania z programu <xref:System.Windows.Application.Resources%2A> .</span><span class="sxs-lookup"><span data-stu-id="ffe77-116">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="ffe77-117">Najpierw *klucz* słownika jest obiektem, dlatego należy użyć dokładnie tego samego wystąpienia obiektu, gdy oba ustawienia i pobierają wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="ffe77-117">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="ffe77-118">(Należy pamiętać, że podczas korzystania z ciągu w kluczu jest rozróżniana wielkość liter). Po drugie, *wartość* słownika jest obiektem, dlatego konieczne będzie przekonwertowanie wartości na żądany typ podczas pobierania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="ffe77-118">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe77-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffe77-119">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="ffe77-120">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="ffe77-120">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="ffe77-121">Połączone słowniki zasobów</span><span class="sxs-lookup"><span data-stu-id="ffe77-121">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
