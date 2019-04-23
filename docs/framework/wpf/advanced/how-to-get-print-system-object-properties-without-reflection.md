---
title: 'Instrukcje: Pobieranie właściwości obiektu systemowego drukowania bez odbicia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: bb906dafd98e75708764b5f0f009900719f6a475
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335202"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="79ce3-102">Instrukcje: Pobieranie właściwości obiektu systemowego drukowania bez odbicia</span><span class="sxs-lookup"><span data-stu-id="79ce3-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="79ce3-103">Pozycjonuj właściwości (i typy tych właściwości) dla obiektu przy użyciu odbicia może zmniejszyć wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="79ce3-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="79ce3-104"><xref:System.Printing.IndexedProperties> Przestrzeń nazw umożliwia pobranie tych informacji przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="79ce3-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79ce3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="79ce3-105">Example</span></span>  
 <span data-ttu-id="79ce3-106">Dostępne są następujące kroki w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="79ce3-106">The steps for doing this are as follows.</span></span>  
  
1. <span data-ttu-id="79ce3-107">Utwórz wystąpienie tego typu.</span><span class="sxs-lookup"><span data-stu-id="79ce3-107">Create an instance of the type.</span></span> <span data-ttu-id="79ce3-108">W poniższym przykładzie typ jest <xref:System.Printing.PrintQueue> typ, który jest dostarczany z programem Microsoft .NET Framework, ale prawie identyczna kodu powinny działać dla typów wyprowadzonych z <xref:System.Printing.PrintSystemObject>.</span><span class="sxs-lookup"><span data-stu-id="79ce3-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with Microsoft .NET Framework, but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2. <span data-ttu-id="79ce3-109">Tworzenie <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z typu <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span><span class="sxs-lookup"><span data-stu-id="79ce3-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="79ce3-110"><xref:System.Collections.DictionaryEntry.Value%2A> Właściwości każdego wpisu, w tym słowniku jest obiektem, jednego z typów pochodnych typu <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="79ce3-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3. <span data-ttu-id="79ce3-111">Wyliczanie elementów członkowskich w słowniku.</span><span class="sxs-lookup"><span data-stu-id="79ce3-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="79ce3-112">Dla każdego z nich wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="79ce3-112">For each of them, do the following.</span></span>  
  
4. <span data-ttu-id="79ce3-113">Wartość każdego wpisu do rzutowania w górę <xref:System.Printing.IndexedProperties.PrintProperty> i użyć go do utworzenia <xref:System.Printing.IndexedProperties.PrintProperty> obiektu.</span><span class="sxs-lookup"><span data-stu-id="79ce3-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5. <span data-ttu-id="79ce3-114">Pobierz typ <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> poszczególnych <xref:System.Printing.IndexedProperties.PrintProperty> obiektu.</span><span class="sxs-lookup"><span data-stu-id="79ce3-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="79ce3-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79ce3-115">See also</span></span>

- <xref:System.Printing.IndexedProperties.PrintProperty>
- <xref:System.Printing.PrintSystemObject>
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [<span data-ttu-id="79ce3-116">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="79ce3-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="79ce3-117">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="79ce3-117">Printing Overview</span></span>](printing-overview.md)
