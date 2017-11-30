---
title: "Jak pobrać właściwości obiektu systemowego drukowania bez odbicia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2f6015d25ee8868fe9b4c6dcf3bf145d413521e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="2f29b-102">Jak pobrać właściwości obiektu systemowego drukowania bez odbicia</span><span class="sxs-lookup"><span data-stu-id="2f29b-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="2f29b-103">Podziel na pozycje właściwości (i typy tych właściwości) w obiekcie za pomocą odbicia może zmniejszyć wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2f29b-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="2f29b-104"><xref:System.Printing.IndexedProperties> Przestrzeni nazw umożliwia pobranie tych informacji przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="2f29b-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f29b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="2f29b-105">Example</span></span>  
 <span data-ttu-id="2f29b-106">Dostępne są następujące kroki, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="2f29b-106">The steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="2f29b-107">Utwórz wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="2f29b-107">Create an instance of the type.</span></span> <span data-ttu-id="2f29b-108">W poniższym przykładzie jest typ <xref:System.Printing.PrintQueue> typu, który jest dostarczany z [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], ale niemal identyczne kodu powinny działać dla typów wyprowadzonych z <xref:System.Printing.PrintSystemObject>.</span><span class="sxs-lookup"><span data-stu-id="2f29b-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2.  <span data-ttu-id="2f29b-109">Utwórz <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z poziomu typu <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f29b-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="2f29b-110"><xref:System.Collections.DictionaryEntry.Value%2A> Właściwości każdego wpisu w tym słowniku jest obiektem jednego z jego typów pochodnych <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="2f29b-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3.  <span data-ttu-id="2f29b-111">Wyliczanie elementów członkowskich w słowniku.</span><span class="sxs-lookup"><span data-stu-id="2f29b-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="2f29b-112">Dla każdego z nich wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="2f29b-112">For each of them, do the following.</span></span>  
  
4.  <span data-ttu-id="2f29b-113">Wartość każdego wpisu do rzutowania w górę <xref:System.Printing.IndexedProperties.PrintProperty> i umożliwia utworzenie <xref:System.Printing.IndexedProperties.PrintProperty> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2f29b-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5.  <span data-ttu-id="2f29b-114">Wybrany typ <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> poszczególnych <xref:System.Printing.IndexedProperties.PrintProperty> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2f29b-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="2f29b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f29b-115">See Also</span></span>  
 <xref:System.Printing.IndexedProperties.PrintProperty>  
 <xref:System.Printing.PrintSystemObject>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="2f29b-116">Dokumentów na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="2f29b-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="2f29b-117">Omówienie drukowania</span><span class="sxs-lookup"><span data-stu-id="2f29b-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
