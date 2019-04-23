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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977655"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a><span data-ttu-id="d6b0a-102">Instrukcje: Utrwalanie i przywracanie właściwości zakresu aplikacji między sesjami aplikacji</span><span class="sxs-lookup"><span data-stu-id="d6b0a-102">How to: Persist and Restore Application-Scope Properties Across Application Sessions</span></span>
<span data-ttu-id="d6b0a-103">W tym przykładzie przedstawiono sposób utrwalanie właściwości zakresu aplikacji podczas zamykania aplikacji i w jaki sposób można przywrócić właściwości zakresu aplikacji, gdy aplikacja jest następnego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="d6b0a-103">This example shows how to persist application-scope properties when an application shuts down, and how to restore application-scope properties when an application is next launch.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6b0a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6b0a-104">Example</span></span>  
 <span data-ttu-id="d6b0a-105">Aplikacja będzie się powtarzał właściwości zakresu aplikacji i przywraca je z magazynu izolowanego.</span><span class="sxs-lookup"><span data-stu-id="d6b0a-105">The application persists application-scope properties to, and restores them from, isolated storage.</span></span> <span data-ttu-id="d6b0a-106">Wydzielona pamięć masowa jest obszar chronionego magazynu, które mogą być bezpiecznie używane przez aplikacje bez uprawnienia dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="d6b0a-106">Isolated storage is a protected storage area that can safely be used by applications without file access permission.</span></span>  <span data-ttu-id="d6b0a-107">*App.xaml* plik definiuje `App_Startup` metodę jako programu obsługi <xref:System.Windows.Application.Startup?displayProperty=nameWithType> zdarzenia i `App_Exit` metodę jako programu obsługi <xref:System.Windows.Application.Exit?displayProperty=nameWithType> zdarzeń, jak pokazano w wyróżnionych wierszy w pierwszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d6b0a-107">The *App.xaml* file defines the `App_Startup` method as the handler for the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event, and the `App_Exit` method as the handler for the  <xref:System.Windows.Application.Exit?displayProperty=nameWithType> event, as shown in the highlighted lines of the first example.</span></span> <span data-ttu-id="d6b0a-108">Drugi przykład przedstawia część *App.xaml.cs* i *App.xaml.vb* pliki, które prezentuje kod `App_Startup` metody, która przywraca właściwości zakresu aplikacji i `App_Exit` metody, która zapisuje właściwości zakresu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d6b0a-108">The second example shows a portion of the *App.xaml.cs* and *App.xaml.vb* files that highlights the code for the `App_Startup` method, which restores application-scope properties, and the `App_Exit` method, which saves application-scope properties.</span></span>

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
