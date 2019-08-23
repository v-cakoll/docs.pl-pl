---
title: Serializacja i metadane
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 937577f86ec854f5a458fe6067836a85a540695a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913803"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="eb85f-102">Serializacja i metadane</span><span class="sxs-lookup"><span data-stu-id="eb85f-102">Serialization and Metadata</span></span>

<span data-ttu-id="eb85f-103">Jeśli aplikacja serializować i deserializacji obiektów, może być konieczne dodanie wpisów do pliku dyrektywy środowiska uruchomieniowego (. Rd. xml) w celu upewnienia się, że niezbędne metadane są obecne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="eb85f-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="eb85f-104">Istnieją dwie kategorie serializatorów, a każdy z nich wymaga innej obsługi w pliku dyrektywy środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="eb85f-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="eb85f-105">Serializatory innych firm oparte na odbiciu.</span><span class="sxs-lookup"><span data-stu-id="eb85f-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="eb85f-106">Wymagają one modyfikacji pliku dyrektywy środowiska uruchomieniowego i zostały omówione w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="eb85f-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="eb85f-107">W bibliotece klas .NET Framework nie znaleziono serializatorów opartych na nieodbiciach.</span><span class="sxs-lookup"><span data-stu-id="eb85f-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="eb85f-108">Mogą one wymagać modyfikacji pliku dyrektywy środowiska uruchomieniowego i zostały omówione w sekcji [serializatory firmy Microsoft](#Microsoft) .</span><span class="sxs-lookup"><span data-stu-id="eb85f-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a><span data-ttu-id="eb85f-109">Serializatory innych firm</span><span class="sxs-lookup"><span data-stu-id="eb85f-109">Third-party serializers</span></span>

 <span data-ttu-id="eb85f-110">Serializatory innych firm, w tym Newtonsoft. JSON, zazwyczaj są oparte na odbiciach.</span><span class="sxs-lookup"><span data-stu-id="eb85f-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="eb85f-111">Przy użyciu binarnego dużego obiektu (BLOB) danych serializowanych pola w danych są przypisywane do konkretnego typu przez wyszukanie pól typu docelowego według nazwy.</span><span class="sxs-lookup"><span data-stu-id="eb85f-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="eb85f-112">Co najmniej przy użyciu tych bibliotek powoduje wyjątki [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) dla każdego <xref:System.Type> obiektu, który próbujesz serializować `List<Type>` lub deserializować w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="eb85f-112">At a minimum, using these libraries causes [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="eb85f-113">Najprostszym sposobem rozwiązania problemów spowodowanych brakiem metadanych dla tych serializatorów jest zbieranie typów, które będą używane w serializacji w ramach pojedynczej przestrzeni nazw (na `App.Models`przykład) i `Serialize` zastosowanie dyrektywy Metadata do niej:</span><span class="sxs-lookup"><span data-stu-id="eb85f-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="eb85f-114">Aby uzyskać informacje o składni używanej w tym przykładzie, zobacz [ \<Namespace > element](../../../docs/framework/net-native/namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="eb85f-114">For information about the syntax used in the example, see [\<Namespace> Element](../../../docs/framework/net-native/namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a><span data-ttu-id="eb85f-115">Serializatory firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="eb85f-115">Microsoft serializers</span></span>

 <span data-ttu-id="eb85f-116">Chociaż klasy <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> i<xref:System.Xml.Serialization.XmlSerializer> nie polegają na odbiciu, wymagają generowania kodu na podstawie obiektu do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="eb85f-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="eb85f-117">Przeciążone konstruktory dla każdego serializatora <xref:System.Type> obejmują parametr, który określa typ do serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="eb85f-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="eb85f-118">Sposób określenia tego typu w kodzie definiuje działanie, które należy wykonać, zgodnie z opisem w dwóch następnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="eb85f-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="eb85f-119">wartość typeof użyta w konstruktorze</span><span class="sxs-lookup"><span data-stu-id="eb85f-119">typeof used in the constructor</span></span>

 <span data-ttu-id="eb85f-120">W przypadku wywołania konstruktora tych klas serializacji i dołączenia C# operatora [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) w wywołaniu metody **nie trzeba wykonywać żadnych dodatkowych czynności**.</span><span class="sxs-lookup"><span data-stu-id="eb85f-120">If you call a constructor of these serialization classes and include the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="eb85f-121">Na przykład w każdym z następujących wywołań konstruktora `typeof` klasy serializacji słowo kluczowe jest używane jako część wyrażenia przesłanego do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="eb85f-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="eb85f-122">Kompilator .NET Native automatycznie obsłuży ten kod.</span><span class="sxs-lookup"><span data-stu-id="eb85f-122">The .NET Native compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="eb85f-123">wartość typeof użyta poza konstruktorem</span><span class="sxs-lookup"><span data-stu-id="eb85f-123">typeof used outside the constructor</span></span>

 <span data-ttu-id="eb85f-124">Jeśli wywołasz konstruktora tych klas serializacji i użyjesz C# operatora [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) poza wyrażeniem dostarczonym do <xref:System.Type> parametru konstruktora, jak w poniższym kodzie, kompilator .NET Native nie może rozpoznać typu:</span><span class="sxs-lookup"><span data-stu-id="eb85f-124">If you call a constructor of these serialization classes and use the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the .NET Native compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="eb85f-125">W takim przypadku należy określić typ w pliku dyrektywy środowiska uruchomieniowego, dodając wpis podobny do tego:</span><span class="sxs-lookup"><span data-stu-id="eb85f-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="eb85f-126">Podobnie w przypadku wywołania konstruktora, takiego jak <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> i udostępnienia tablicy dodatkowych <xref:System.Type> obiektów do serializacji, jak w poniższym kodzie, kompilator .NET Native nie może rozpoznać tych typów.</span><span class="sxs-lookup"><span data-stu-id="eb85f-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the .NET Native compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="eb85f-127">Należy dodać następujące wpisy dla każdego typu do pliku dyrektywy środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="eb85f-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="eb85f-128">Aby uzyskać informacje o składni używanej w tym przykładzie, zobacz [ \<Type > element](../../../docs/framework/net-native/type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="eb85f-128">For information about the syntax used in the example, see [\<Type> Element](../../../docs/framework/net-native/type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb85f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb85f-129">See also</span></span>

- [<span data-ttu-id="eb85f-130">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="eb85f-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="eb85f-131">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="eb85f-131">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="eb85f-132">\<Typ > element</span><span class="sxs-lookup"><span data-stu-id="eb85f-132">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="eb85f-133">\<Przestrzeń nazw > element</span><span class="sxs-lookup"><span data-stu-id="eb85f-133">\<Namespace> Element</span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)
