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
ms.locfileid: "33544501"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Jak użyć ResourceDictionary, aby zarządzać zlokalizowanymi zasobami ciągów
Ten przykład przedstawia sposób użycia <xref:System.Windows.ResourceDictionary> do zasobów ciągu Lokalizowalny pakietu dla aplikacji Windows Presentation Foundation (WPF).  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Na potrzeby zarządzania zasobami Lokalizowalny ciąg ResourceDictionary  
  
1.  Utwórz <xref:System.Windows.ResourceDictionary> zawiera ciągi chcesz do zlokalizowania. Poniższy kod przedstawia przykład.  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     Ten kod definiuje zasób ciągu `localizedMessage`, typu <xref:System.String>, z <xref:System> przestrzeni nazw w pliku mscorlib.dll.  
  
2.  Dodaj <xref:System.Windows.ResourceDictionary> do aplikacji, używając następującego kodu.  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  Użyj zasobu ciągu z poziomu znacznika, przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] podobnie do następującego.  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  Użyj zasobu ciągu z kodem, przy użyciu kodu podobne do następujących.  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  Lokalizowanie aplikacji. Aby uzyskać więcej informacji, zobacz [lokalizowanie aplikacji](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).
