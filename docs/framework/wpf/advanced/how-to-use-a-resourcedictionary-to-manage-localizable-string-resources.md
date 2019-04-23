---
title: 'Instrukcje: Używanie elementu ResourceDictionary do zarządzania lokalizowalnymi zasobami ciągów'
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
ms.openlocfilehash: b56a307ed31fc8f7573215eac70350ac5e4b9de1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772118"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Instrukcje: Używanie elementu ResourceDictionary do zarządzania lokalizowalnymi zasobami ciągów
W tym przykładzie pokazano, jak używać <xref:System.Windows.ResourceDictionary> do pakietu zlokalizowanymi zasobami ciągów dla aplikacji Windows Presentation Foundation (WPF).  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Aby użyć ResourceDictionary, aby zarządzać zlokalizowanymi zasobami ciągów  
  
1. Utwórz <xref:System.Windows.ResourceDictionary> zawierającą ciągi, które chcesz zlokalizować. Poniższy kod przedstawia przykład.  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     Ten kod definiuje zasób ciągu `localizedMessage`, typu <xref:System.String>, z <xref:System> przestrzeni nazw w mscorlib.dll.  
  
2. Dodaj <xref:System.Windows.ResourceDictionary> do aplikacji, używając następującego kodu.  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3. Użyj zasobu ciągu z kodu znaczników, za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] podobnie do następującego.  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4. Korzystając z zasobu ciągu z kodem, przy użyciu kodu, jak pokazano poniżej.  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5. Lokalizowanie aplikacji. Aby uzyskać więcej informacji, zobacz [lokalizowanie aplikacji](how-to-localize-an-application.md).
