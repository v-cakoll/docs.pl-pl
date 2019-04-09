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
ms.openlocfilehash: 99b04060d4e7c14313655010dc4fbd5ce1c90487
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134956"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a>Instrukcje: Utrwalanie i przywracanie właściwości zakresu aplikacji między sesjami aplikacji
W tym przykładzie przedstawiono sposób utrwalanie właściwości zakresu aplikacji podczas zamykania aplikacji i w jaki sposób można przywrócić właściwości zakresu aplikacji, gdy aplikacja jest następnego uruchomienia.  
  
## <a name="example"></a>Przykład  
 Aplikacja będzie się powtarzał właściwości zakresu aplikacji i przywraca je z magazynu izolowanego. Wydzielona pamięć masowa jest obszar chronionego magazynu, które mogą być bezpiecznie używane przez aplikacje bez uprawnienia dostępu do pliku.  *App.xaml* plik definiuje `App_Startup` metodę jako programu obsługi <xref:System.Windows.Application.Startup?displayProperty=nameWithType> zdarzenia i `App_Exit` metodę jako programu obsługi <xref:System.Windows.Application.Exit?displayProperty=nameWithType> zdarzeń, jak pokazano w wyróżnionych wierszy w pierwszym przykładzie. Drugi przykład przedstawia część *App.xaml.cs* i *App.xaml.vb* pliki, które prezentuje kod `App_Startup` metody, która przywraca właściwości zakresu aplikacji i `App_Exit` metody, która zapisuje właściwości zakresu aplikacji.

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
