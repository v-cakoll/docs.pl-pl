---
title: Serializacja i metadane
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e4db59da7a17e47b8e3df939ec64f5124e04454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395976"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="192b6-102">Serializacja i metadane</span><span class="sxs-lookup"><span data-stu-id="192b6-102">Serialization and Metadata</span></span>
<span data-ttu-id="192b6-103">Jeśli aplikacja serializuje i deserializuje obiektów, może być konieczne dodanie wpisów do Twojej dyrektyw środowiska uruchomieniowego (. rd.xml) pliku, aby upewnić się, że metadane potrzebne jest obecny w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="192b6-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="192b6-104">Istnieją dwie kategorie serializatorów i każdy z nich wymaga innej obsługi w pliku dyrektyw środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="192b6-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
-   <span data-ttu-id="192b6-105">Oparty na odbiciu serializatorów innych firm.</span><span class="sxs-lookup"><span data-stu-id="192b6-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="192b6-106">Są wymagają modyfikacji pliku dyrektyw środowiska uruchomieniowego które opisano w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="192b6-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
-   <span data-ttu-id="192b6-107">Odbicie nie na podstawie serializatorów w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="192b6-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="192b6-108">Są mogą wymagać modyfikacji pliku dyrektyw środowiska uruchomieniowego które zostały omówione w [serializatorów Microsoft](#Microsoft) sekcji.</span><span class="sxs-lookup"><span data-stu-id="192b6-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a><span data-ttu-id="192b6-109">Serializatorów innych firm</span><span class="sxs-lookup"><span data-stu-id="192b6-109">Third-party serializers</span></span>  
 <span data-ttu-id="192b6-110">Serializatorów innych części, w tym Newtonsoft.JSON, zazwyczaj są oparty na odbiciu.</span><span class="sxs-lookup"><span data-stu-id="192b6-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="192b6-111">Podana dużego obiektu binarnego (BLOB) serializowanych danych, pola w danych są przypisane do konkretnego typu według pola Typ docelowy według nazwy.</span><span class="sxs-lookup"><span data-stu-id="192b6-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="192b6-112">Co najmniej przy użyciu biblioteki powoduje [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) wyjątków dla każdego <xref:System.Type> obiekt, który zostanie podjęta próba serializacji lub deserializacji w `List<Type>` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="192b6-112">At a minimum, using these libraries causes [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="192b6-113">Najprostszym sposobem, aby rozwiązać problemy spowodowane przez Brak metadanych dla tych serializatorów jest zbieranie typy, które będą używane w serializacji w jednej przestrzeni nazw (takich jak `App.Models`) i zastosować `Serialize` dyrektywy metadanych:</span><span class="sxs-lookup"><span data-stu-id="192b6-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="192b6-114">Informacje o składni używanej w tym przykładzie, zobacz [ \<Namespace > elementu](../../../docs/framework/net-native/namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="192b6-114">For information about the syntax used in the example, see [\<Namespace> Element](../../../docs/framework/net-native/namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a><span data-ttu-id="192b6-115">Microsoft serializatorów</span><span class="sxs-lookup"><span data-stu-id="192b6-115">Microsoft serializers</span></span>  
 <span data-ttu-id="192b6-116">Mimo że <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer> klas, nie należy polegać na podstawie odbicia, wymagają one będzie generowany kod na podstawie obiektu serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="192b6-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="192b6-117">Przeciążone konstruktory dla każdego serializator obejmują <xref:System.Type> parametr określający typ serializacji lub deserializacji.</span><span class="sxs-lookup"><span data-stu-id="192b6-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="192b6-118">Sposób określania typu w kodzie definiuje akcji, które należy podjąć, zgodnie z opisem w dwóch następnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="192b6-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="192b6-119">TypeOf używany w Konstruktorze</span><span class="sxs-lookup"><span data-stu-id="192b6-119">typeof used in the constructor</span></span>  
 <span data-ttu-id="192b6-120">Jeśli można wywołać konstruktora z tych klas serializacji i obejmują C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) — słowo kluczowe w wywołaniu metody **nie trzeba wykonywać żadnych dodatkowych działań**.</span><span class="sxs-lookup"><span data-stu-id="192b6-120">If you call a constructor of these serialization classes and include the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="192b6-121">Na przykład w każdej z następujących wywołania konstruktora klasy serializacji `typeof` słowo kluczowe jest używane jako część wyrażenia przekazany do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="192b6-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="192b6-122">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilatora będzie automatycznie obsługiwał tego kodu.</span><span class="sxs-lookup"><span data-stu-id="192b6-122">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="192b6-123">TypeOf używane poza konstruktora</span><span class="sxs-lookup"><span data-stu-id="192b6-123">typeof used outside the constructor</span></span>  
 <span data-ttu-id="192b6-124">Można wywołać konstruktora z tych klas serializacji i używać języka C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) — słowo kluczowe poza wyrażeniem przekazany do konstruktora <xref:System.Type> parametru zgodnie z poniższym kodem [!INCLUDE[net_native](../../../includes/net-native-md.md)] nie kompilatora Aby usunąć typ:</span><span class="sxs-lookup"><span data-stu-id="192b6-124">If you call a constructor of these serialization classes and use the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="192b6-125">W takim przypadku należy określić typ pliku dyrektyw środowiska uruchomieniowego, dodając wpis następująco:</span><span class="sxs-lookup"><span data-stu-id="192b6-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="192b6-126">Podobnie jeśli takie jak wywołać konstruktora <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> i podaj tablicę dodatkowe <xref:System.Type> obiekty do serializacji, zgodnie z poniższym kodem [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilatora nie można rozpoznać typu.</span><span class="sxs-lookup"><span data-stu-id="192b6-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="192b6-127">Wpisy, takich jak dla każdego typu należy dodać do pliku dyrektyw środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="192b6-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="192b6-128">Informacje o składni używanej w tym przykładzie, zobacz [ \<typu > elementu](../../../docs/framework/net-native/type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="192b6-128">For information about the syntax used in the example, see [\<Type> Element](../../../docs/framework/net-native/type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="192b6-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="192b6-129">See Also</span></span>  
 [<span data-ttu-id="192b6-130">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="192b6-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="192b6-131">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="192b6-131">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="192b6-132">\<Typ > — Element</span><span class="sxs-lookup"><span data-stu-id="192b6-132">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="192b6-133">\<Namespace > — Element</span><span class="sxs-lookup"><span data-stu-id="192b6-133">\<Namespace> Element</span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)
