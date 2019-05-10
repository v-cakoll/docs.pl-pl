---
title: Serializacja i metadane
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e7a8e6509cea5f9035e3b8544aa37aa99681822
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650313"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="8ee00-102">Serializacja i metadane</span><span class="sxs-lookup"><span data-stu-id="8ee00-102">Serialization and Metadata</span></span>
<span data-ttu-id="8ee00-103">Jeśli Twoja aplikacja serializuje i deserializuje obiektów, konieczne może być dodawanie wpisów do Twojej dyrektywy środowiska uruchomieniowego (. rd.xml) plik, aby upewnić się, że metadane potrzebne znajduje się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8ee00-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="8ee00-104">Istnieją dwie kategorie serializatory, a każdy z nich wymaga innej obsługi w pliku dyrektyw środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="8ee00-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="8ee00-105">Oparty na odbiciu serializatory innych firm.</span><span class="sxs-lookup"><span data-stu-id="8ee00-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="8ee00-106">Te wymagają modyfikacji pliku dyrektyw środowiska uruchomieniowego i zostały omówione w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="8ee00-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="8ee00-107">Odbicie inne niż oparte serializatory znalezione w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ee00-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="8ee00-108">Te mogą wymagać modyfikacji pliku dyrektyw środowiska uruchomieniowego, zostały one omówione w [serializatory Microsoft](#Microsoft) sekcji.</span><span class="sxs-lookup"><span data-stu-id="8ee00-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a><span data-ttu-id="8ee00-109">Serializatory innych firm</span><span class="sxs-lookup"><span data-stu-id="8ee00-109">Third-party serializers</span></span>  
 <span data-ttu-id="8ee00-110">Serializatory firm trzecich, w tym Newtonsoft.JSON, są zazwyczaj oparty na odbiciu.</span><span class="sxs-lookup"><span data-stu-id="8ee00-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="8ee00-111">Biorąc pod uwagę duży obiekt binarny (BLOB) serializowanych danych, pól danych są przypisane do konkretnego typu przez wyszukanie pola typu docelowego według nazwy.</span><span class="sxs-lookup"><span data-stu-id="8ee00-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="8ee00-112">Jako minimum, korzystania z tych bibliotek powoduje, że [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątki dla poszczególnych <xref:System.Type> obiekt, który próbujesz serializacji lub deserializacji w `List<Type>` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8ee00-112">At a minimum, using these libraries causes [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="8ee00-113">Najprostszym sposobem, aby rozwiązać problemy spowodowane przez Brak metadanych dla tych serializatory ma zbierać typy, które będą używane w serializacji w ramach jednej przestrzeni nazw (takich jak `App.Models`) i Zastosuj `Serialize` dyrektywy metadanych:</span><span class="sxs-lookup"><span data-stu-id="8ee00-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="8ee00-114">Aby uzyskać informacje dotyczące składni użytych w tym przykładzie, zobacz [ \<Namespace > Element](../../../docs/framework/net-native/namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="8ee00-114">For information about the syntax used in the example, see [\<Namespace> Element](../../../docs/framework/net-native/namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a><span data-ttu-id="8ee00-115">Serializatory firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="8ee00-115">Microsoft serializers</span></span>  
 <span data-ttu-id="8ee00-116">Mimo że <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer> klasy, nie należy polegać na podstawie odbicia, wymagają one generowania kodu na podstawie obiektu serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="8ee00-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="8ee00-117">Przeciążenia konstruktorów dla każdego elementu serializującego obejmują <xref:System.Type> parametr, który określa typ serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="8ee00-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="8ee00-118">Jak określić typu w kodzie definiuje akcję, którą należy wykonać, zgodnie z opisem w dwóch następnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="8ee00-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="8ee00-119">TypeOf używany w Konstruktorze</span><span class="sxs-lookup"><span data-stu-id="8ee00-119">typeof used in the constructor</span></span>  
 <span data-ttu-id="8ee00-120">Możesz wywołać konstruktora klasy te serializacji i obejmują C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) — słowo kluczowe w wywołaniu metody **nie trzeba wykonywać żadnych dodatkowych działań**.</span><span class="sxs-lookup"><span data-stu-id="8ee00-120">If you call a constructor of these serialization classes and include the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="8ee00-121">Na przykład w każdym z następujących wywołania konstruktora klasy serializacji `typeof` słowo kluczowe jest używane jako część wyrażenia przekazany do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="8ee00-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="8ee00-122">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilator będzie automatycznie obsługiwać ten kod.</span><span class="sxs-lookup"><span data-stu-id="8ee00-122">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="8ee00-123">TypeOf używany poza konstruktora</span><span class="sxs-lookup"><span data-stu-id="8ee00-123">typeof used outside the constructor</span></span>  
 <span data-ttu-id="8ee00-124">Możesz wywołać konstruktora klasy te serializacji i używać C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) — słowo kluczowe poza wyrażenie dostarczane do konstruktora <xref:System.Type> parametru, zgodnie z poniższym kodem [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilatora Nie można rozpoznać typu:</span><span class="sxs-lookup"><span data-stu-id="8ee00-124">If you call a constructor of these serialization classes and use the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="8ee00-125">W takim przypadku należy określić typ w plik dyrektywy środowiska uruchomieniowego, dodając wpis podobny do tego:</span><span class="sxs-lookup"><span data-stu-id="8ee00-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="8ee00-126">Podobnie jeśli takie jak wywołać konstruktora <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> i zapewniają szereg dodatkowych <xref:System.Type> obiekty do serializacji, tak jak w poniższym kodzie [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilator nie może rozpoznać te typy.</span><span class="sxs-lookup"><span data-stu-id="8ee00-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="8ee00-127">Należy dodać wpisy podobny do następującego dla każdego typu pliku dyrektyw środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="8ee00-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="8ee00-128">Aby uzyskać informacje dotyczące składni użytych w tym przykładzie, zobacz [ \<typ > Element](../../../docs/framework/net-native/type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="8ee00-128">For information about the syntax used in the example, see [\<Type> Element](../../../docs/framework/net-native/type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ee00-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ee00-129">See also</span></span>

- [<span data-ttu-id="8ee00-130">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="8ee00-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="8ee00-131">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="8ee00-131">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="8ee00-132">\<Typ > Element</span><span class="sxs-lookup"><span data-stu-id="8ee00-132">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="8ee00-133">\<Namespace > Element</span><span class="sxs-lookup"><span data-stu-id="8ee00-133">\<Namespace> Element</span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)
