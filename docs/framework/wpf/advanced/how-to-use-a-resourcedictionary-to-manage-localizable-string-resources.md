---
title: Jak użyć ResourceDictionary, aby zarządzać zlokalizowanymi zasobami ciągów
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
ms.openlocfilehash: 76ff3f688b5d3e7122254990076edb21fe6ae119
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="779f2-102">Jak użyć ResourceDictionary, aby zarządzać zlokalizowanymi zasobami ciągów</span><span class="sxs-lookup"><span data-stu-id="779f2-102">How to: Use a ResourceDictionary to Manage Localizable String Resources</span></span>
<span data-ttu-id="779f2-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.ResourceDictionary> do zasobów ciągu Lokalizowalny pakietu dla aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="779f2-103">This example shows how to use a <xref:System.Windows.ResourceDictionary> to package localizable string resources for Windows Presentation Foundation (WPF) applications.</span></span>  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="779f2-104">Na potrzeby zarządzania zasobami Lokalizowalny ciąg ResourceDictionary</span><span class="sxs-lookup"><span data-stu-id="779f2-104">To use a ResourceDictionary to manage localizable string resources</span></span>  
  
1.  <span data-ttu-id="779f2-105">Utwórz <xref:System.Windows.ResourceDictionary> zawiera ciągi chcesz do zlokalizowania.</span><span class="sxs-lookup"><span data-stu-id="779f2-105">Create a <xref:System.Windows.ResourceDictionary> that contains the strings you would like to localize.</span></span> <span data-ttu-id="779f2-106">Poniższy kod przedstawia przykład.</span><span class="sxs-lookup"><span data-stu-id="779f2-106">The following code shows an example.</span></span>  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     <span data-ttu-id="779f2-107">Ten kod definiuje zasób ciągu `localizedMessage`, typu <xref:System.String>, z <xref:System> przestrzeni nazw w pliku mscorlib.dll.</span><span class="sxs-lookup"><span data-stu-id="779f2-107">This code defines a string resource, `localizedMessage`, of type <xref:System.String>, from the <xref:System> namespace in mscorlib.dll.</span></span>  
  
2.  <span data-ttu-id="779f2-108">Dodaj <xref:System.Windows.ResourceDictionary> do aplikacji, używając następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="779f2-108">Add the <xref:System.Windows.ResourceDictionary> to your application, using the following code.</span></span>  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  <span data-ttu-id="779f2-109">Użyj zasobu ciągu z poziomu znacznika, przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] podobnie do następującego.</span><span class="sxs-lookup"><span data-stu-id="779f2-109">Use the string resource from markup, using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] like the following.</span></span>  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  <span data-ttu-id="779f2-110">Użyj zasobu ciągu z kodem, przy użyciu kodu podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="779f2-110">Use the string resource from code-behind, using code like the following.</span></span>  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  <span data-ttu-id="779f2-111">Lokalizowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="779f2-111">Localize the application.</span></span> <span data-ttu-id="779f2-112">Aby uzyskać więcej informacji, zobacz [lokalizowanie aplikacji](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="779f2-112">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>
