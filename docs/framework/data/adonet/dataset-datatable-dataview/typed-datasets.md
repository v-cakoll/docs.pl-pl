---
title: Typizowane zbiory danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e3d5edc4f469b59ff787e500ad447fe0076c332c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="typed-datasets"></a><span data-ttu-id="36d57-102">Typizowane zbiory danych</span><span class="sxs-lookup"><span data-stu-id="36d57-102">Typed DataSets</span></span>
<span data-ttu-id="36d57-103">Wraz z późne powiązania dostęp do wartości za pośrednictwem słabo zmienne typu <xref:System.Data.DataSet> zapewnia dostęp do danych za pośrednictwem jednoznacznie metaphor.</span><span class="sxs-lookup"><span data-stu-id="36d57-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="36d57-104">Tabele i kolumny, które są częścią **DataSet** można uzyskać dostęp za pomocą nazw przyjaznych dla użytkownika i silnie typizowane zmiennych.</span><span class="sxs-lookup"><span data-stu-id="36d57-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="36d57-105">Typizowany **DataSet** jest klasą pochodną **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="36d57-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="36d57-106">W efekcie dziedziczy wszystkie metody, zdarzeń i właściwości **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="36d57-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="36d57-107">Ponadto maszynowy **DataSet** udostępnia silnie typizowane metody, zdarzeń i właściwości.</span><span class="sxs-lookup"><span data-stu-id="36d57-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="36d57-108">Oznacza to, że są dostępne tabele i kolumny według nazwy, zamiast za pomocą metody opartej na kolekcji.</span><span class="sxs-lookup"><span data-stu-id="36d57-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="36d57-109">Jako uzupełnienie Ulepszona czytelność kodu, typu **DataSet** umożliwia również kodu programu Visual Studio .NET edytora automatycznie wypełnić wierszy podczas pisania.</span><span class="sxs-lookup"><span data-stu-id="36d57-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="36d57-110">Ponadto silnie typizowaną **DataSet** zapewnia dostęp do wartości jako poprawnego typu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="36d57-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="36d57-111">Z silnie typizowaną **DataSet**, błędy niezgodności typów są przechwytywane, gdy kod jest skompilowany, a nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="36d57-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36d57-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="36d57-112">In This Section</span></span>  
 [<span data-ttu-id="36d57-113">Generowanie silnie Typizowane zbiory danych</span><span class="sxs-lookup"><span data-stu-id="36d57-113">Generating Strongly Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 <span data-ttu-id="36d57-114">Opisuje sposób tworzenia i używania silnie typizowaną **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="36d57-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="36d57-115">Dodawanie adnotacji do Typizowane zbiory danych</span><span class="sxs-lookup"><span data-stu-id="36d57-115">Annotating Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 <span data-ttu-id="36d57-116">Opisuje, jak dodawać adnotacje schematu języka (XSD) definicja schematu XML służący do generowania silnie typizowaną do **DataSet**, aby zapewnić **zestawu danych** przyjaznych nazw elementów bez zmiany podstawowego schematu.</span><span class="sxs-lookup"><span data-stu-id="36d57-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d57-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36d57-117">See Also</span></span>  
 [<span data-ttu-id="36d57-118">Zbiory danych, DataTables i DataViews</span><span class="sxs-lookup"><span data-stu-id="36d57-118">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="36d57-119">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="36d57-119">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
