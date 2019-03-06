---
title: 'Instrukcje: Użyj ResourceDictionary, aby zarządzać zlokalizowanymi zasobami ciągów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
ms.openlocfilehash: e28086d8c97070b854ebdea35fe347c64c5cd7ac
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377940"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="3425e-102">Instrukcje: Użyj ResourceDictionary, aby zarządzać zlokalizowanymi zasobami ciągów</span><span class="sxs-lookup"><span data-stu-id="3425e-102">How to: Use a ResourceDictionary to Manage Localizable String Resources</span></span>
<span data-ttu-id="3425e-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.ResourceDictionary> do pakietu zlokalizowanymi zasobami ciągów dla aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="3425e-103">This example shows how to use a <xref:System.Windows.ResourceDictionary> to package localizable string resources for Windows Presentation Foundation (WPF) applications.</span></span>  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="3425e-104">Aby użyć ResourceDictionary, aby zarządzać zlokalizowanymi zasobami ciągów</span><span class="sxs-lookup"><span data-stu-id="3425e-104">To use a ResourceDictionary to manage localizable string resources</span></span>  
  
1.  <span data-ttu-id="3425e-105">Utwórz <xref:System.Windows.ResourceDictionary> zawierającą ciągi, które chcesz zlokalizować.</span><span class="sxs-lookup"><span data-stu-id="3425e-105">Create a <xref:System.Windows.ResourceDictionary> that contains the strings you would like to localize.</span></span> <span data-ttu-id="3425e-106">Poniższy kod przedstawia przykład.</span><span class="sxs-lookup"><span data-stu-id="3425e-106">The following code shows an example.</span></span>  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     <span data-ttu-id="3425e-107">Ten kod definiuje zasób ciągu `localizedMessage`, typu <xref:System.String>, z <xref:System> przestrzeni nazw w mscorlib.dll.</span><span class="sxs-lookup"><span data-stu-id="3425e-107">This code defines a string resource, `localizedMessage`, of type <xref:System.String>, from the <xref:System> namespace in mscorlib.dll.</span></span>  
  
2.  <span data-ttu-id="3425e-108">Dodaj <xref:System.Windows.ResourceDictionary> do aplikacji, używając następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="3425e-108">Add the <xref:System.Windows.ResourceDictionary> to your application, using the following code.</span></span>  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  <span data-ttu-id="3425e-109">Użyj zasobu ciągu z kodu znaczników, za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] podobnie do następującego.</span><span class="sxs-lookup"><span data-stu-id="3425e-109">Use the string resource from markup, using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] like the following.</span></span>  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  <span data-ttu-id="3425e-110">Korzystając z zasobu ciągu z kodem, przy użyciu kodu, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="3425e-110">Use the string resource from code-behind, using code like the following.</span></span>  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  <span data-ttu-id="3425e-111">Lokalizowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3425e-111">Localize the application.</span></span> <span data-ttu-id="3425e-112">Aby uzyskać więcej informacji, zobacz [lokalizowanie aplikacji](how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="3425e-112">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>
