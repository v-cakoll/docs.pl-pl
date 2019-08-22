---
title: 'Instrukcje: Utrwalanie i przywracanie właściwości zakresu aplikacji między sesjami aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application-scope properties [WPF], persisting
- persisting application-scope properties [WPF]
- properties [WPF], persisting
- restoring application-scope properties [WPF]
- properties [WPF], restoring
- application-scope properties [WPF], restoring
ms.assetid: 55d5904a-f444-4eb5-abd3-6bc74dd14226
ms.openlocfilehash: d9c2dda2745e7528902b6b1c4f46d17264d1a8d8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666730"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a>Instrukcje: Utrwalanie i przywracanie właściwości zakresu aplikacji między sesjami aplikacji
Ten przykład pokazuje, jak utrzymać właściwości zakresu aplikacji podczas zamykania aplikacji oraz jak przywrócić właściwości zakresu aplikacji po następnym uruchomieniu aplikacji.  
  
## <a name="example"></a>Przykład  
 Aplikacja utrzymuje właściwości zakresu aplikacji do i przywraca je z magazynu izolowanego. Magazyn izolowany to chroniony obszar magazynu, który może być bezpiecznie używany przez aplikacje bez uprawnień dostępu do plików.  Plik *App. XAML* definiuje `App_Startup` metodę jako procedurę obsługi dla <xref:System.Windows.Application.Startup?displayProperty=nameWithType> zdarzenia i `App_Exit` metodę jako procedurę obsługi dla <xref:System.Windows.Application.Exit?displayProperty=nameWithType> zdarzenia, jak pokazano w wyróżnionych wierszach pierwszego przykładu. W drugim przykładzie przedstawiono część plików *App.XAML.cs* i *App. XAML. vb* , która podświetla `App_Startup` kod dla metody, która przywraca właściwości zakresu aplikacji i `App_Exit` metodę, która zapisuje zakres aplikacji aœciwoœci.

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=14-45)]
