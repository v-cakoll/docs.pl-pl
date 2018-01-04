---
title: 'Porady: mapowania hierarchii dziedziczenia'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 93f3eb40e96c0735218464c8ee69a3e6fe358a03
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="dcef3-102">Porady: mapowania hierarchii dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="dcef3-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="dcef3-103">Aby zaimplementować mapowania dziedziczenia w [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], należy określić atrybuty i właściwości atrybutu dla klasy głównym hierarchii dziedziczenia zgodnie z opisem w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="dcef3-103">To implement inheritance mapping in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="dcef3-104">Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do mapowania hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="dcef3-104">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span> <span data-ttu-id="dcef3-105">Zobacz [porady: Konfigurowanie dziedziczenia za pomocą Projektanta obiektów relacyjnych](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="dcef3-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dcef3-106">Na podklasy są wymagane nie specjalne atrybutów lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcef3-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="dcef3-107">Pamiętaj, szczególnie podklasy nie mają <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="dcef3-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="dcef3-108">Do mapowania hierarchii dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="dcef3-108">To map an inheritance hierarchy</span></span>  
  
1.  <span data-ttu-id="dcef3-109">Dodaj <xref:System.Data.Linq.Mapping.TableAttribute> do klasy głównym atrybutu.</span><span class="sxs-lookup"><span data-stu-id="dcef3-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2.  <span data-ttu-id="dcef3-110">Również do klasy głównym, należy dodać <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu dla każdej klasy, struktury hierarchii.</span><span class="sxs-lookup"><span data-stu-id="dcef3-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3.  <span data-ttu-id="dcef3-111">Dla każdego <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu, zdefiniuj <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcef3-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="dcef3-112">Ta właściwość ma wartość, która pojawia się w tabeli bazy danych w <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> kolumny, która wskazuje, które klasy lub podklasy ten wiersz danych należy.</span><span class="sxs-lookup"><span data-stu-id="dcef3-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4.  <span data-ttu-id="dcef3-113">Dla każdego <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu, należy również dodać <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcef3-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="dcef3-114">Ta właściwość ma wartość, która określa, które klasy lub podklasy oznacza wartość klucza.</span><span class="sxs-lookup"><span data-stu-id="dcef3-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5.  <span data-ttu-id="dcef3-115">Tylko na jednym z <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybuty, Dodaj <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="dcef3-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="dcef3-116">Ta właściwość służy do wyznaczania *rezerwowy* mapowania, gdy wartość dyskryminatora z tabeli bazy danych nie jest zgodna z żadną <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> wartość mapowań dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="dcef3-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6.  <span data-ttu-id="dcef3-117">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="dcef3-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="dcef3-118">Ta właściwość oznacza, że jest to kolumna, która przechowuje <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> wartość.</span><span class="sxs-lookup"><span data-stu-id="dcef3-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcef3-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="dcef3-119">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dcef3-120">Jeśli używasz [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] skonfigurować dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="dcef3-120">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to configure inheritance.</span></span> <span data-ttu-id="dcef3-121">Zobacz [porady: Konfigurowanie dziedziczenia za pomocą Projektanta obiektów relacyjnych](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="dcef3-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="dcef3-122">W poniższym przykładzie kodu `Vehicle` jest zdefiniowany jako klasy głównym i poprzednie kroki zostały wdrożone do opisywania hierarchia [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dcef3-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="dcef3-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dcef3-123">See Also</span></span>  
 [<span data-ttu-id="dcef3-124">Obsługa dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="dcef3-124">Inheritance Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)  
 [<span data-ttu-id="dcef3-125">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="dcef3-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
