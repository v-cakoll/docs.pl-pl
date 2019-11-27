---
title: Właściwość wartości XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 571d9130ef69df580bbba5d90bc8758b4b627196
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349419"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="53c1a-102">Właściwość wartości XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53c1a-102">XML Value Property (Visual Basic)</span></span>

<span data-ttu-id="53c1a-103">Zapewnia dostęp do wartości pierwszego elementu kolekcji obiektów <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="53c1a-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="53c1a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53c1a-104">Syntax</span></span>

```vb
object.Value
```

## <a name="parts"></a><span data-ttu-id="53c1a-105">Części</span><span class="sxs-lookup"><span data-stu-id="53c1a-105">Parts</span></span>

|<span data-ttu-id="53c1a-106">Termin</span><span class="sxs-lookup"><span data-stu-id="53c1a-106">Term</span></span>|<span data-ttu-id="53c1a-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="53c1a-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="53c1a-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="53c1a-108">Required.</span></span> <span data-ttu-id="53c1a-109">Kolekcja obiektów <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="53c1a-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  

## <a name="return-value"></a><span data-ttu-id="53c1a-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="53c1a-110">Return Value</span></span>

 <span data-ttu-id="53c1a-111">`String`, który zawiera wartość pierwszego elementu kolekcji lub `Nothing`, jeśli kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="53c1a-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>

## <a name="remarks"></a><span data-ttu-id="53c1a-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53c1a-112">Remarks</span></span>

 <span data-ttu-id="53c1a-113">Właściwość <xref:System.Xml.Linq.XElement.Value%2A> ułatwia dostęp do wartości pierwszego elementu w kolekcji obiektów <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="53c1a-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="53c1a-114">Ta właściwość najpierw sprawdza, czy kolekcja zawiera co najmniej jeden obiekt.</span><span class="sxs-lookup"><span data-stu-id="53c1a-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="53c1a-115">Jeśli kolekcja jest pusta, ta właściwość zwraca `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="53c1a-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="53c1a-116">W przeciwnym razie ta właściwość zwraca wartość właściwości <xref:System.Xml.Linq.XElement.Value%2A> pierwszego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="53c1a-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="53c1a-117">Po uzyskaniu dostępu do wartości atrybutu XML przy użyciu identyfikatora "\@" wartość atrybutu jest zwracana jako `String` i nie trzeba jawnie określać właściwości <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="53c1a-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>

 <span data-ttu-id="53c1a-118">Aby uzyskać dostęp do innych elementów w kolekcji, można użyć właściwości indeksatora rozszerzenia XML.</span><span class="sxs-lookup"><span data-stu-id="53c1a-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="53c1a-119">Aby uzyskać więcej informacji, zobacz [Extension Indexer właściwości](extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="53c1a-119">For more information, see [Extension Indexer Property](extension-indexer-property.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="53c1a-120">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="53c1a-120">Inheritance</span></span>

 <span data-ttu-id="53c1a-121">Większość użytkowników nie będzie musiała implementować <xref:System.Collections.Generic.IEnumerable%601>i w związku z tym można zignorować tę sekcję.</span><span class="sxs-lookup"><span data-stu-id="53c1a-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>

 <span data-ttu-id="53c1a-122">Właściwość <xref:System.Xml.Linq.XElement.Value%2A> jest właściwością rozszerzenia dla typów, które implementują `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="53c1a-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="53c1a-123">Powiązanie tej właściwości rozszerzenia jest podobne do powiązania metod rozszerzających: Jeśli typ implementuje jeden z interfejsów i definiuje właściwość o nazwie "value", ta właściwość ma pierwszeństwo przed właściwością rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="53c1a-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="53c1a-124">Innymi słowy, ta właściwość <xref:System.Xml.Linq.XElement.Value%2A> może być zastąpiona przez zdefiniowanie nowej właściwości w klasie implementującej `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="53c1a-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>

## <a name="example"></a><span data-ttu-id="53c1a-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="53c1a-125">Example</span></span>

 <span data-ttu-id="53c1a-126">Poniższy przykład pokazuje, jak używać właściwości <xref:System.Xml.Linq.XElement.Value%2A>, aby uzyskać dostęp do pierwszego węzła w kolekcji obiektów <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="53c1a-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="53c1a-127">W przykładzie użyta jest właściwość oś podrzędna do pobrania kolekcji wszystkich węzłów podrzędnych o nazwie `phone`, które znajdują się w obiekcie `contact`.</span><span class="sxs-lookup"><span data-stu-id="53c1a-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 <span data-ttu-id="53c1a-128">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="53c1a-128">This code displays the following text:</span></span>

 `Phone number: 206-555-0144`

## <a name="example"></a><span data-ttu-id="53c1a-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="53c1a-129">Example</span></span>

 <span data-ttu-id="53c1a-130">Poniższy przykład pokazuje, jak pobrać wartość atrybutu XML z kolekcji obiektów <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="53c1a-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="53c1a-131">W przykładzie jest stosowana Właściwość osi atrybutu do wyświetlania wartości atrybutu `type` dla wszystkich elementów `phone`.</span><span class="sxs-lookup"><span data-stu-id="53c1a-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 <span data-ttu-id="53c1a-132">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="53c1a-132">This code displays the following text:</span></span>

 ```console
 home
 work
```

## <a name="see-also"></a><span data-ttu-id="53c1a-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53c1a-133">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="53c1a-134">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="53c1a-134">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="53c1a-135">Literały XML</span><span class="sxs-lookup"><span data-stu-id="53c1a-135">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="53c1a-136">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53c1a-136">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="53c1a-137">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="53c1a-137">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="53c1a-138">Właściwość indeksatora rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="53c1a-138">Extension Indexer Property</span></span>](extension-indexer-property.md)
- [<span data-ttu-id="53c1a-139">Właściwości osi elementu podrzędnego XML</span><span class="sxs-lookup"><span data-stu-id="53c1a-139">XML Child Axis Property</span></span>](xml-child-axis-property.md)
- [<span data-ttu-id="53c1a-140">Właściwości osi atrybutu XML</span><span class="sxs-lookup"><span data-stu-id="53c1a-140">XML Attribute Axis Property</span></span>](xml-attribute-axis-property.md)
