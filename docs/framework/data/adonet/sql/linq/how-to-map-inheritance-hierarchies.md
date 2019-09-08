---
title: 'Instrukcje: Mapowanie hierarchii dziedziczenia'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1366e8f5f79a8e695e52c405e20a894861453ae7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781767"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="b9ad4-102">Instrukcje: Mapowanie hierarchii dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="b9ad4-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="b9ad4-103">Aby zaimplementować mapowanie dziedziczenia [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]w programie, należy określić atrybuty i właściwości atrybutów w klasie głównej hierarchii dziedziczenia zgodnie z opisem w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-103">To implement inheritance mapping in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="b9ad4-104">Deweloperzy korzystający z programu Visual Studio mogą mapować hierarchie dziedziczenia przy użyciu Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-104">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="b9ad4-105">Zobacz [How to: Skonfiguruj dziedziczenie przy użyciu narzędzia O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)Designer.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9ad4-106">Dla podklas nie są wymagane żadne specjalne atrybuty ani właściwości.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="b9ad4-107">Należy zwrócić uwagę na <xref:System.Data.Linq.Mapping.TableAttribute> to, że podklasy nie mają atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="b9ad4-108">Aby zmapować hierarchię dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="b9ad4-108">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="b9ad4-109"><xref:System.Data.Linq.Mapping.TableAttribute> Dodaj atrybut do klasy głównej.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="b9ad4-110">Także do klasy głównej, Dodaj <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybut dla każdej klasy w strukturze hierarchii.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="b9ad4-111">Dla każdego <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> Zdefiniuj właściwość.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="b9ad4-112">Ta właściwość zawiera wartość, która pojawia się w tabeli bazy danych w <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> kolumnie, aby wskazać klasę lub podklasę, do której należy ten wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="b9ad4-113">Dla każdego <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutu, należy również <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> dodać właściwość.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="b9ad4-114">Ta właściwość zawiera wartość określającą klasę lub podklasę wartość klucza.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="b9ad4-115">Tylko jeden z <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atrybutów, <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> Dodaj właściwość.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="b9ad4-116">Ta właściwość służy do wyznaczania mapowania *rezerwowego* , gdy wartość rozróżniacza z tabeli bazy danych nie <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> jest zgodna z żadną wartością w mapowaniu dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="b9ad4-117"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> dla atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="b9ad4-118">Ta właściwość oznacza, że jest to kolumna, która zawiera <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> wartość.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9ad4-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9ad4-119">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9ad4-120">Jeśli używasz programu Visual Studio, możesz użyć Object Relational Designer, aby skonfigurować dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="b9ad4-120">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="b9ad4-121">Zobacz [How to: Konfigurowanie dziedziczenia za pomocą narzędzia Object Relational Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="b9ad4-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="b9ad4-122">W poniższym przykładzie `Vehicle` kodu jest zdefiniowany jako Klasa główna, a poprzednie kroki zostały zaimplementowane w celu opisania hierarchii dla programu [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b9ad4-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b9ad4-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9ad4-123">See also</span></span>

- [<span data-ttu-id="b9ad4-124">Obsługa dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="b9ad4-124">Inheritance Support</span></span>](inheritance-support.md)
- [<span data-ttu-id="b9ad4-125">Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu</span><span class="sxs-lookup"><span data-stu-id="b9ad4-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
