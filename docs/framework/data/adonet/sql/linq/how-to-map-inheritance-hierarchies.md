---
title: 'Instrukcje: mapowanie hierarchii dziedziczenia'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 737cb8743d8fd9c93cd46ebf50fba3fe554a35f2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634667"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="77f66-102">Instrukcje: mapowanie hierarchii dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="77f66-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="77f66-103">Aby zaimplementować mapowanie dziedziczenia w LINQ, należy określić atrybuty i właściwości atrybutów w klasie głównej hierarchii dziedziczenia, zgodnie z opisem w poniższych krokach.</span><span class="sxs-lookup"><span data-stu-id="77f66-103">To implement inheritance mapping in LINQ, you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="77f66-104">Deweloperzy korzystający z programu Visual Studio mogą mapować hierarchie dziedziczenia przy użyciu Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="77f66-104">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="77f66-105">Zobacz [jak: Konfigurowanie dziedziczenia przy użyciu narzędzia O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="77f66-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77f66-106">Dla podklas nie są wymagane żadne specjalne atrybuty ani właściwości.</span><span class="sxs-lookup"><span data-stu-id="77f66-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="77f66-107">Należy zwrócić uwagę na to, że podklasy nie mają atrybutu <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="77f66-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="77f66-108">Aby zmapować hierarchię dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="77f66-108">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="77f66-109">Dodaj atrybut <xref:System.Data.Linq.Mapping.TableAttribute> do klasy głównej.</span><span class="sxs-lookup"><span data-stu-id="77f66-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="77f66-110">Także do klasy głównej, Dodaj atrybut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> dla każdej klasy w strukturze hierarchii.</span><span class="sxs-lookup"><span data-stu-id="77f66-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="77f66-111">Dla każdego atrybutu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, zdefiniuj Właściwość <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.</span><span class="sxs-lookup"><span data-stu-id="77f66-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="77f66-112">Ta właściwość zawiera wartość, która pojawia się w tabeli bazy danych w kolumnie <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>, aby wskazać klasę lub podklasę, do której należy ten wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="77f66-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="77f66-113">Dla każdego atrybutu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> należy również dodać właściwość <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>.</span><span class="sxs-lookup"><span data-stu-id="77f66-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="77f66-114">Ta właściwość zawiera wartość określającą klasę lub podklasę wartość klucza.</span><span class="sxs-lookup"><span data-stu-id="77f66-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="77f66-115">Tylko jeden z atrybutów <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> Dodaj właściwość <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>.</span><span class="sxs-lookup"><span data-stu-id="77f66-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="77f66-116">Ta właściwość służy do wyznaczania mapowania *rezerwowego* , gdy wartość rozróżniacza z tabeli bazy danych nie jest zgodna z żadną <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> wartością w mapowaniu dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="77f66-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="77f66-117">Dodaj właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> dla atrybutu <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="77f66-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="77f66-118">Ta właściwość oznacza, że jest to kolumna, która zawiera wartość <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.</span><span class="sxs-lookup"><span data-stu-id="77f66-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77f66-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="77f66-119">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77f66-120">Jeśli używasz programu Visual Studio, możesz użyć Object Relational Designer, aby skonfigurować dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="77f66-120">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="77f66-121">Zobacz [jak: Konfigurowanie dziedziczenia przy użyciu projektanta o/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="77f66-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="77f66-122">W poniższym przykładzie kodu `Vehicle` jest definiowana jako Klasa główna, a poprzednie kroki zostały zaimplementowane w celu opisania hierarchii dla LINQ.</span><span class="sxs-lookup"><span data-stu-id="77f66-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for LINQ.</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="77f66-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77f66-123">See also</span></span>

- [<span data-ttu-id="77f66-124">Obsługa dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="77f66-124">Inheritance Support</span></span>](inheritance-support.md)
- [<span data-ttu-id="77f66-125">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="77f66-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
