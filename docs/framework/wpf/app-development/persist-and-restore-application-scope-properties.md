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
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a><span data-ttu-id="a1ea5-102">Instrukcje: Utrwalanie i przywracanie właściwości zakresu aplikacji między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="a1ea5-102">How to: Persist and Restore Application-Scope Properties Across Application Sessions</span></span>
<span data-ttu-id="a1ea5-103">Ten przykład pokazuje, jak utrzymać właściwości zakresu aplikacji podczas zamykania aplikacji oraz jak przywrócić właściwości zakresu aplikacji po następnym uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a1ea5-103">This example shows how to persist application-scope properties when an application shuts down, and how to restore application-scope properties when an application is next launch.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1ea5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1ea5-104">Example</span></span>  
 <span data-ttu-id="a1ea5-105">Aplikacja utrzymuje właściwości zakresu aplikacji do i przywraca je z magazynu izolowanego.</span><span class="sxs-lookup"><span data-stu-id="a1ea5-105">The application persists application-scope properties to, and restores them from, isolated storage.</span></span> <span data-ttu-id="a1ea5-106">Magazyn izolowany to chroniony obszar magazynu, który może być bezpiecznie używany przez aplikacje bez uprawnień dostępu do plików.</span><span class="sxs-lookup"><span data-stu-id="a1ea5-106">Isolated storage is a protected storage area that can safely be used by applications without file access permission.</span></span>  <span data-ttu-id="a1ea5-107">Plik *App. XAML* definiuje `App_Startup` metodę jako procedurę obsługi dla <xref:System.Windows.Application.Startup?displayProperty=nameWithType> zdarzenia i `App_Exit` metodę jako procedurę obsługi dla <xref:System.Windows.Application.Exit?displayProperty=nameWithType> zdarzenia, jak pokazano w wyróżnionych wierszach pierwszego przykładu.</span><span class="sxs-lookup"><span data-stu-id="a1ea5-107">The *App.xaml* file defines the `App_Startup` method as the handler for the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event, and the `App_Exit` method as the handler for the  <xref:System.Windows.Application.Exit?displayProperty=nameWithType> event, as shown in the highlighted lines of the first example.</span></span> <span data-ttu-id="a1ea5-108">W drugim przykładzie przedstawiono część plików *App.XAML.cs* i *App. XAML. vb* , która podświetla `App_Startup` kod dla metody, która przywraca właściwości zakresu aplikacji i `App_Exit` metodę, która zapisuje zakres aplikacji aœciwoœci.</span><span class="sxs-lookup"><span data-stu-id="a1ea5-108">The second example shows a portion of the *App.xaml.cs* and *App.xaml.vb* files that highlights the code for the `App_Startup` method, which restores application-scope properties, and the `App_Exit` method, which saves application-scope properties.</span></span>

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=14-45)]
