---
title: Serializacja i metadane
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: 1805b6ca06d584237303d1366222419da3e8b9ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128122"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="bcfb6-102">Serializacja i metadane</span><span class="sxs-lookup"><span data-stu-id="bcfb6-102">Serialization and Metadata</span></span>

<span data-ttu-id="bcfb6-103">Jeśli aplikacja serializować i deserializacji obiektów, może być konieczne dodanie wpisów do pliku dyrektywy środowiska uruchomieniowego (. Rd. xml) w celu upewnienia się, że niezbędne metadane są obecne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="bcfb6-104">Istnieją dwie kategorie serializatorów, a każdy z nich wymaga innej obsługi w pliku dyrektywy środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="bcfb6-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="bcfb6-105">Serializatory innych firm oparte na odbiciu.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="bcfb6-106">Wymagają one modyfikacji pliku dyrektywy środowiska uruchomieniowego i zostały omówione w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="bcfb6-107">W bibliotece klas .NET Framework nie znaleziono serializatorów opartych na nieodbiciach.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="bcfb6-108">Mogą one wymagać modyfikacji pliku dyrektywy środowiska uruchomieniowego i zostały omówione w sekcji [serializatory firmy Microsoft](#Microsoft) .</span><span class="sxs-lookup"><span data-stu-id="bcfb6-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a><span data-ttu-id="bcfb6-109">Serializatory innych firm</span><span class="sxs-lookup"><span data-stu-id="bcfb6-109">Third-party serializers</span></span>

 <span data-ttu-id="bcfb6-110">Serializatory innych firm, w tym Newtonsoft. JSON, zazwyczaj są oparte na odbiciach.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="bcfb6-111">Przy użyciu binarnego dużego obiektu (BLOB) danych serializowanych pola w danych są przypisywane do konkretnego typu przez wyszukanie pól typu docelowego według nazwy.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="bcfb6-112">Co najmniej przy użyciu tych bibliotek powoduje wyjątki [MissingMetadataException](missingmetadataexception-class-net-native.md) dla każdego obiektu <xref:System.Type>, który próbujesz serializować lub deserializować w kolekcji `List<Type>`.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-112">At a minimum, using these libraries causes [MissingMetadataException](missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="bcfb6-113">Najprostszym sposobem rozwiązania problemów spowodowanych brakiem metadanych dla tych serializatorów jest zbieranie typów, które będą używane w serializacji w ramach pojedynczej przestrzeni nazw (na przykład `App.Models`), i zastosowanie dyrektywy metadanych `Serialize`:</span><span class="sxs-lookup"><span data-stu-id="bcfb6-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="bcfb6-114">Aby uzyskać informacje o składni używanej w przykładzie, zobacz [\<Namespace > element](namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="bcfb6-114">For information about the syntax used in the example, see [\<Namespace> Element](namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a><span data-ttu-id="bcfb6-115">Serializatory firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="bcfb6-115">Microsoft serializers</span></span>

 <span data-ttu-id="bcfb6-116">Mimo że klasy <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>i <xref:System.Xml.Serialization.XmlSerializer> nie polegają na odbiciu, wymagają generowania kodu na podstawie obiektu do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="bcfb6-117">Przeciążone konstruktory dla każdego serializatora zawierają parametr <xref:System.Type>, który określa typ do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="bcfb6-118">Sposób określenia tego typu w kodzie definiuje działanie, które należy wykonać, zgodnie z opisem w dwóch następnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="bcfb6-119">wartość typeof użyta w konstruktorze</span><span class="sxs-lookup"><span data-stu-id="bcfb6-119">typeof used in the constructor</span></span>

 <span data-ttu-id="bcfb6-120">W przypadku wywołania konstruktora tych klas serializacji i dołączenia C# operatora [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) w wywołaniu metody **nie trzeba wykonywać żadnych dodatkowych czynności**.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-120">If you call a constructor of these serialization classes and include the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="bcfb6-121">Na przykład w każdym z następujących wywołań konstruktora klasy serializacji słowo kluczowe `typeof` jest używane jako część wyrażenia przesłanego do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="bcfb6-122">Kompilator .NET Native automatycznie obsłuży ten kod.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-122">The .NET Native compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="bcfb6-123">wartość typeof użyta poza konstruktorem</span><span class="sxs-lookup"><span data-stu-id="bcfb6-123">typeof used outside the constructor</span></span>

 <span data-ttu-id="bcfb6-124">Jeśli wywołasz konstruktora tych klas serializacji i użyjesz C# operatora [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) poza wyrażeniem dostarczonym do parametru <xref:System.Type> konstruktora, jak w poniższym kodzie, kompilator .NET Native nie może rozpoznać typu:</span><span class="sxs-lookup"><span data-stu-id="bcfb6-124">If you call a constructor of these serialization classes and use the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the .NET Native compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="bcfb6-125">W takim przypadku należy określić typ w pliku dyrektywy środowiska uruchomieniowego, dodając wpis podobny do tego:</span><span class="sxs-lookup"><span data-stu-id="bcfb6-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="bcfb6-126">Podobnie, jeśli wywołasz konstruktora, takiego jak <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> i dostarczysz tablicę dodatkowych obiektów <xref:System.Type> do serializacji, jak w poniższym kodzie, kompilator .NET Native nie będzie mógł rozpoznać tych typów.</span><span class="sxs-lookup"><span data-stu-id="bcfb6-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the .NET Native compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="bcfb6-127">Należy dodać następujące wpisy dla każdego typu do pliku dyrektywy środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="bcfb6-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="bcfb6-128">Aby uzyskać informacje o składni używanej w tym przykładzie, zobacz [\<Type > elementu](type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="bcfb6-128">For information about the syntax used in the example, see [\<Type> Element](type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcfb6-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bcfb6-129">See also</span></span>

- [<span data-ttu-id="bcfb6-130">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="bcfb6-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="bcfb6-131">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="bcfb6-131">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="bcfb6-132">Typ\<> element</span><span class="sxs-lookup"><span data-stu-id="bcfb6-132">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="bcfb6-133">\<> elementu przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="bcfb6-133">\<Namespace> Element</span></span>](namespace-element-net-native.md)
