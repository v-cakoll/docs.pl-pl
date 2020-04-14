---
title: Serializacja i metadane
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: 7c6fe241fbf92f52abfa0eb66c37bff4d227b4e5
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81241922"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="9138e-102">Serializacja i metadane</span><span class="sxs-lookup"><span data-stu-id="9138e-102">Serialization and Metadata</span></span>

<span data-ttu-id="9138e-103">Jeśli aplikacja serializuje i deserializes obiektów, może być konieczne dodanie wpisów do pliku dyrektywy środowiska uruchomieniowego (.rd.xml), aby upewnić się, że niezbędne metadane są obecne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9138e-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="9138e-104">Istnieją dwie kategorie serializatorów, a każda z nich wymaga innej obsługi w pliku dyrektyw środowiska wykonawczego:</span><span class="sxs-lookup"><span data-stu-id="9138e-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="9138e-105">Serializatory innych firm oparte na odbiciach.</span><span class="sxs-lookup"><span data-stu-id="9138e-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="9138e-106">Wymagają one modyfikacji pliku dyrektyw środowiska wykonawczego i zostały omówione w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9138e-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="9138e-107">Serializatory oparte na braku odbicia znalezione w bibliotece klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9138e-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="9138e-108">Mogą one wymagać modyfikacji pliku dyrektyw środowiska wykonawczego i są omówione w sekcji [serializatory firmy Microsoft.](#Microsoft)</span><span class="sxs-lookup"><span data-stu-id="9138e-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a><span data-ttu-id="9138e-109">Serializatory innych firm</span><span class="sxs-lookup"><span data-stu-id="9138e-109">Third-party serializers</span></span>

 <span data-ttu-id="9138e-110">Serializatory trzeciej części, w tym Newtonsoft.JSON, zazwyczaj są oparte na refleksji.</span><span class="sxs-lookup"><span data-stu-id="9138e-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="9138e-111">Biorąc pod uwagę binarny duży obiekt (BLOB) z serializowanych danych, pola w danych są przypisywane do typu betonowego, wyszukując pola typu docelowego według nazwy.</span><span class="sxs-lookup"><span data-stu-id="9138e-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="9138e-112">Co najmniej przy użyciu tych bibliotek powoduje [MissingMetadataException](missingmetadataexception-class-net-native.md) wyjątki dla każdego <xref:System.Type> obiektu, który `List<Type>` próbujesz serializować lub deserialize w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9138e-112">At a minimum, using these libraries causes [MissingMetadataException](missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="9138e-113">Najprostszym sposobem rozwiązania problemów spowodowanych brakującymi metadanymi dla tych serializatorów jest zbieranie typów, które `App.Models`będą używane `Serialize` w serializacji w ramach pojedynczego obszaru nazw (na przykład) i stosowanie do niej dyrektywy metadanych:</span><span class="sxs-lookup"><span data-stu-id="9138e-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="9138e-114">Aby uzyskać informacje na temat składni [ \<](namespace-element-net-native.md)używanej w przykładzie, zobacz Obszar nazw> element .</span><span class="sxs-lookup"><span data-stu-id="9138e-114">For information about the syntax used in the example, see [\<Namespace> Element](namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a><span data-ttu-id="9138e-115">Serializatory firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="9138e-115">Microsoft serializers</span></span>

 <span data-ttu-id="9138e-116">Chociaż <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>i <xref:System.Xml.Serialization.XmlSerializer> klasy nie opierają się na odbicie, wymagają kodu do wygenerowania na podstawie obiektu, który ma być serializowany lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="9138e-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="9138e-117">Przeciążonych konstruktorów dla każdego <xref:System.Type> serializatora zawierają parametr, który określa typ, który ma być serializowany lub deserialized.</span><span class="sxs-lookup"><span data-stu-id="9138e-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="9138e-118">Sposób określenia tego typu w kodzie definiuje akcję, którą należy podjąć, jak opisano w następnych dwóch sekcjach.</span><span class="sxs-lookup"><span data-stu-id="9138e-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="9138e-119">typeof używane w konstruktorze</span><span class="sxs-lookup"><span data-stu-id="9138e-119">typeof used in the constructor</span></span>

 <span data-ttu-id="9138e-120">Jeśli wywołasz konstruktor tych klas serializacji i uwzględnisz operator [typu](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) C# w wywołaniu metody, **nie musisz wykonywać żadnej dodatkowej pracy.**</span><span class="sxs-lookup"><span data-stu-id="9138e-120">If you call a constructor of these serialization classes and include the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="9138e-121">Na przykład w każdym z następujących wywołań do konstruktora klasy `typeof` serializacji, słowo kluczowe jest używane jako część wyrażenia przekazywane do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="9138e-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="9138e-122">Kompilator natywny platformy .NET automatycznie obsłuży ten kod.</span><span class="sxs-lookup"><span data-stu-id="9138e-122">The .NET Native compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="9138e-123">typeof używane poza konstruktorem</span><span class="sxs-lookup"><span data-stu-id="9138e-123">typeof used outside the constructor</span></span>

 <span data-ttu-id="9138e-124">Jeśli wywołasz konstruktor tych klas serializacji i użyjesz operatora [typu](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) C# <xref:System.Type> poza wyrażeniem dostarczonym do parametru konstruktora, jak w poniższym kodzie, kompilator .NET Native nie może rozwiązać tego typu:</span><span class="sxs-lookup"><span data-stu-id="9138e-124">If you call a constructor of these serialization classes and use the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the .NET Native compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="9138e-125">W takim przypadku należy określić typ w pliku dyrektyw środowiska wykonawczego, dodając wpis w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="9138e-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="9138e-126">Podobnie jeśli wywołasz konstruktora, takich jak <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> <xref:System.Type> i podać tablicę dodatkowych obiektów do serializacji, jak w poniższym kodzie, .NET natywnego kompilatora nie może rozwiązać tych typów.</span><span class="sxs-lookup"><span data-stu-id="9138e-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the .NET Native compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="9138e-127">Do pliku dyrektyw środowiska wykonawczego należy dodać wpisy, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="9138e-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="9138e-128">Aby uzyskać informacje na temat składni [ \<](type-element-net-native.md)używanej w przykładzie, zobacz Typ> Element .</span><span class="sxs-lookup"><span data-stu-id="9138e-128">For information about the syntax used in the example, see [\<Type> Element](type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9138e-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9138e-129">See also</span></span>

- [<span data-ttu-id="9138e-130">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="9138e-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9138e-131">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9138e-131">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="9138e-132">\<Wpisz element></span><span class="sxs-lookup"><span data-stu-id="9138e-132">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="9138e-133">\<Element> przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="9138e-133">\<Namespace> Element</span></span>](namespace-element-net-native.md)
