---
title: 'Instrukcje: Mapowanie hierarchii dziedziczenia'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: f75c7fe701c4a2fab1f993517828b38e5a26e2bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138089"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="56ebf-102">Instrukcje: Mapowanie hierarchii dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="56ebf-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="56ebf-103">Aby zaimplementować mapowanie dziedziczenia w [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], należy określić atrybuty i właściwości atrybutów w klasie głównego hierarchii dziedziczenia zgodnie z opisem w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="56ebf-103">To implement inheritance mapping in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="56ebf-104">Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do mapowanie hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="56ebf-104">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span> <span data-ttu-id="56ebf-105">Zobacz [jak: Skonfigurować dziedziczenie za pomocą Projektanta obiektów relacyjnych](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="56ebf-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56ebf-106">Na podklasy są wymagane nie atrybuty specjalne lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="56ebf-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="56ebf-107">Szczególnie Pamiętaj, że podklasy nie mają <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="56ebf-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="56ebf-108">Aby zamapować Hierarchia dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="56ebf-108">To map an inheritance hierarchy</span></span>  
  
1.  <span data-ttu-id="56ebf-109">Dodaj <xref:System.Data.Linq.Mapping.TableAttribute> do katalogu głównego klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="56ebf-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2.  <span data-ttu-id="56ebf-110">Również do klasy głównej, należy dodać <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu dla każdej klasy, struktury hierarchii.</span><span class="sxs-lookup"><span data-stu-id="56ebf-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3.  <span data-ttu-id="56ebf-111">Dla każdego <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu, zdefiniuj <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="56ebf-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="56ebf-112">Ta właściwość zawiera wartość, która pojawia się w tabeli bazy danych w <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> kolumny, aby wskazać, która klasa lub podklasę tego wiersza danych należy do.</span><span class="sxs-lookup"><span data-stu-id="56ebf-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4.  <span data-ttu-id="56ebf-113">Dla każdego <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu, należy również dodać <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="56ebf-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="56ebf-114">Ta właściwość zawiera wartość, która określa, która klasa lub podklasy oznacza wartość klucza.</span><span class="sxs-lookup"><span data-stu-id="56ebf-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5.  <span data-ttu-id="56ebf-115">Tylko na jednym z <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybuty, dodawania <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="56ebf-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="56ebf-116">Ta właściwość służy do wyznaczenia *rezerwowego* mapowania, gdy wartość dyskryminatora z tabeli bazy danych nie pasuje do żadnego <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> wartość w mapowaniach dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="56ebf-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6.  <span data-ttu-id="56ebf-117">Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="56ebf-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="56ebf-118">Tej właściwości oznacza, że jest to kolumna, która przechowuje <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> wartość.</span><span class="sxs-lookup"><span data-stu-id="56ebf-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56ebf-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="56ebf-119">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56ebf-120">Jeśli używasz programu Visual Studio, możesz użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Aby skonfigurować dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="56ebf-120">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to configure inheritance.</span></span> <span data-ttu-id="56ebf-121">Zobacz [jak: Konfigurowanie dziedziczenia za pomocą narzędzia Object Relational Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="56ebf-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="56ebf-122">W poniższym przykładzie kodu `Vehicle` jest zdefiniowany jako Klasa główna i poprzednie kroki zostały wdrożone do opisania hierarchia [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56ebf-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="56ebf-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56ebf-123">See also</span></span>

- [<span data-ttu-id="56ebf-124">Obsługa dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="56ebf-124">Inheritance Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [<span data-ttu-id="56ebf-125">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="56ebf-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
