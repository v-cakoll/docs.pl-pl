---
title: "Znane typy kontraktów danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cdb9e539d16b874ffd37b8e381757594561386e7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="data-contract-known-types"></a><span data-ttu-id="aefc0-102">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="aefc0-102">Data Contract Known Types</span></span>
<span data-ttu-id="aefc0-103"><xref:System.Runtime.Serialization.KnownTypeAttribute> Klasa pozwala na określenie z wyprzedzeniem, typów, które powinny zostać uwzględnione w brany pod uwagę podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="aefc0-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="aefc0-104">Na przykład pracy, zobacz [znane typy](../../../../docs/framework/wcf/samples/known-types.md) przykład.</span><span class="sxs-lookup"><span data-stu-id="aefc0-104">For a working example, see the [Known Types](../../../../docs/framework/wcf/samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="aefc0-105">Zwykle podczas przekazywania parametrów i zwracanych wartości między klientem a usługą, oba punkty końcowe udostępnianie wszystkie kontrakty danych z danych przekazywanych.</span><span class="sxs-lookup"><span data-stu-id="aefc0-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="aefc0-106">Jednak to nie jest to w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="aefc0-106">However, this is not the case in the following circumstances:</span></span>  
  
-   <span data-ttu-id="aefc0-107">Kontrakt danych wysłanych jest pochodną kontraktu oczekiwane dane.</span><span class="sxs-lookup"><span data-stu-id="aefc0-107">The sent data contract is derived from the expected data contract.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="aefc0-108">sekcja o dziedziczenia w [równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span><span class="sxs-lookup"><span data-stu-id="aefc0-108"> the section about inheritance in [Data Contract Equivalence](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span></span> <span data-ttu-id="aefc0-109">W takim przypadku przesyłanych danych nie ma tych samych danych kontraktu, zgodnie z oczekiwaniami odbierania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="aefc0-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
-   <span data-ttu-id="aefc0-110">Deklarowany typ informacji przekazywanych jest interfejsem, w przeciwieństwie do klasy, struktury lub wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="aefc0-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="aefc0-111">W związku z tym ona nie być znane z wyprzedzeniem typ implementuje interfejs faktycznie jest wysyłany, a w związku z tym odbierania punktu końcowego nie może wcześniej określić kontraktu danych przesyłanych danych.</span><span class="sxs-lookup"><span data-stu-id="aefc0-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
-   <span data-ttu-id="aefc0-112">Deklarowany typ informacji przekazywanych jest <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="aefc0-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="aefc0-113">Ponieważ każdy typ dziedziczy z <xref:System.Object>i go nie może być znane z wyprzedzeniem typu faktycznie jest wysyłane, odbierania punktu końcowego nie może określić wcześniej kontraktu danych dla przekazywanych danych.</span><span class="sxs-lookup"><span data-stu-id="aefc0-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="aefc0-114">Jest to szczególnych przypadkach pierwszego elementu: co kontraktu danych pochodzi od domyślnej, generowany dla kontraktu danych puste <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="aefc0-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
-   <span data-ttu-id="aefc0-115">Niektóre typy, które obejmują [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, mieć elementów członkowskich, które znajdują się w jednej z poprzednich trzech kategorii.</span><span class="sxs-lookup"><span data-stu-id="aefc0-115">Some types, which include [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="aefc0-116">Na przykład <xref:System.Collections.Hashtable> używa <xref:System.Object> do przechowywania rzeczywistych obiektów w tablicy skrótów.</span><span class="sxs-lookup"><span data-stu-id="aefc0-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="aefc0-117">Podczas serializowania te typy, po stronie odbierającej nie można ustalić wcześniej kontraktu danych dla tych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="aefc0-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="aefc0-118">Klasa KnownTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="aefc0-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="aefc0-119">Po odebraniu danych odbierania punktu końcowego, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] środowiska uruchomieniowego podejmuje próbę deserializacji danych do wystąpienia typu wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="aefc0-119">When data arrives at a receiving endpoint, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="aefc0-120">Typ, który zostanie uruchomiony do deserializacji jest wybierany przez pierwsze badanie kontraktu komunikatu przychodzącego określenie danych, do którego zawartość komunikatu jest zgodna z.</span><span class="sxs-lookup"><span data-stu-id="aefc0-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="aefc0-121">Aparat deserializacji następnie próbuje odnaleźć typu CLR, który implementuje kontrakt danych zgodne z treść komunikatu.</span><span class="sxs-lookup"><span data-stu-id="aefc0-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="aefc0-122">Zestaw typów kandydujących, które umożliwia aparat deserializacji w trakcie tego procesu jest określana jako zestaw Deserializator "znanych typów."</span><span class="sxs-lookup"><span data-stu-id="aefc0-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="aefc0-123">Jednym ze sposobów let aparat deserializacji wiedzieć o typie polega na użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="aefc0-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="aefc0-124">Ten atrybut nie można zastosować do poszczególnych danych elementów członkowskich, tylko na typy kontraktu danych całego.</span><span class="sxs-lookup"><span data-stu-id="aefc0-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="aefc0-125">Ten atrybut jest stosowany do *typu zewnętrznego* które może być klasą lub strukturą.</span><span class="sxs-lookup"><span data-stu-id="aefc0-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="aefc0-126">W jego najbardziej podstawowa użycia stosowania ten atrybut określa typ jako "znanego typu".</span><span class="sxs-lookup"><span data-stu-id="aefc0-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="aefc0-127">Powoduje to znanego typu jako część zestawu znanych typów, gdy obiekt typu zewnętrznego lub deserializacji dowolny obiekt określony przez jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="aefc0-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="aefc0-128">Więcej niż jeden <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybut można stosować do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="aefc0-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="aefc0-129">Znane typy i elementy podstawowe</span><span class="sxs-lookup"><span data-stu-id="aefc0-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="aefc0-130">Typy pierwotne, jak również niektórych typów traktowane jako typów podstawowych (na przykład <xref:System.DateTime> i <xref:System.Xml.XmlElement>) są zawsze "Nieznany" i nigdy nie muszą być dodane przez ten mechanizm.</span><span class="sxs-lookup"><span data-stu-id="aefc0-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="aefc0-131">Jednak tablice typów pierwotnych muszą być jawnie dodane.</span><span class="sxs-lookup"><span data-stu-id="aefc0-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="aefc0-132">Większość kolekcji są traktowane jako równoważne tablic.</span><span class="sxs-lookup"><span data-stu-id="aefc0-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="aefc0-133">(Inne niż ogólne kolekcje są traktowane jako równoważne tablice <xref:System.Object>).</span><span class="sxs-lookup"><span data-stu-id="aefc0-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="aefc0-134">Na przykład za pomocą podstawowych, tablice pierwotne i pierwotny kolekcji, zobacz przykład 4.</span><span class="sxs-lookup"><span data-stu-id="aefc0-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aefc0-135">W odróżnieniu od innych typów pierwotnych <xref:System.DateTimeOffset> struktury nie jest znanym typem domyślnie, dlatego należy ręcznie dodać do listy znanych typów.</span><span class="sxs-lookup"><span data-stu-id="aefc0-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="aefc0-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="aefc0-136">Examples</span></span>  
 <span data-ttu-id="aefc0-137">W poniższych przykładach pokazano <xref:System.Runtime.Serialization.KnownTypeAttribute> klasy w użyciu.</span><span class="sxs-lookup"><span data-stu-id="aefc0-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="aefc0-138">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="aefc0-138">Example 1</span></span>  
 <span data-ttu-id="aefc0-139">Istnieją trzy klasy z relacji dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="aefc0-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="aefc0-140">Następujące `CompanyLogo` klasy może być Zserializowany, ale nie można przeprowadzić deserializacji Jeśli `ShapeOfLogo` elementu członkowskiego jest ustawiona jako `CircleType` lub `TriangleType` obiektu, ponieważ aparat deserializacji nie rozpoznaje wszystkie typy z nazw kontraktu danych " Koło"lub"Trójkąt."</span><span class="sxs-lookup"><span data-stu-id="aefc0-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="aefc0-141">Prawidłowy sposób zapisu `CompanyLogo` typu przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="aefc0-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="aefc0-142">Zawsze, gdy typu zewnętrznego `CompanyLogo2` jest poddawany deserializacji aparat deserializacji wie o `CircleType` i `TriangleType` i dlatego jest w stanie znaleźć pasujące typy kontraktów danych "Okrąg" i "Trójkąt".</span><span class="sxs-lookup"><span data-stu-id="aefc0-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="aefc0-143">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="aefc0-143">Example 2</span></span>  
 <span data-ttu-id="aefc0-144">W poniższym przykładzie nawet jeśli zarówno `CustomerTypeA` i `CustomerTypeB` ma `Customer` kontraktu danych, wystąpienia `CustomerTypeB` jest tworzony po każdej zmianie `PurchaseOrder` jest deserializacji, ponieważ tylko `CustomerTypeB` jest znana Aparat wykonywania deserializacji.</span><span class="sxs-lookup"><span data-stu-id="aefc0-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="aefc0-145">Przykład 3</span><span class="sxs-lookup"><span data-stu-id="aefc0-145">Example 3</span></span>  
 <span data-ttu-id="aefc0-146">W poniższym przykładzie <xref:System.Collections.Hashtable> przechowuje zawartością wewnętrznie jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="aefc0-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="aefc0-147">Aby pomyślnie zdeserializowanie tablicy skrótów, aparat deserializacji trzeba znać zestaw możliwych typów, które mogą wystąpić istnieje.</span><span class="sxs-lookup"><span data-stu-id="aefc0-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="aefc0-148">W takim przypadku wiemy z wyprzedzeniem jedynie `Book` i `Magazine` obiekty są przechowywane w `Catalog`, więc te są dodawane przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="aefc0-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="aefc0-149">Przykład 4</span><span class="sxs-lookup"><span data-stu-id="aefc0-149">Example 4</span></span>  
 <span data-ttu-id="aefc0-150">W poniższym przykładzie kontraktu danych przechowuje numer i operacji do wykonania na liczbę.</span><span class="sxs-lookup"><span data-stu-id="aefc0-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="aefc0-151">`Numbers` Elementu członkowskiego danych może być liczbą całkowitą, tablica liczb całkowitych, lub <xref:System.Collections.Generic.List%601> zawierający liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="aefc0-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="aefc0-152">Działa tylko po stronie klienta jeśli SVCUTIL. EXE służy do generowania serwer proxy usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="aefc0-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="aefc0-153">NARZĘDZIA SVCUTIL. EXE pobiera metadane z usługi, w tym wszystkie znane typy.</span><span class="sxs-lookup"><span data-stu-id="aefc0-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="aefc0-154">Bez tych informacji klient nie będzie mógł zdeserializować typów.</span><span class="sxs-lookup"><span data-stu-id="aefc0-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="aefc0-155">To jest kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aefc0-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="aefc0-156">Znane typy, dziedziczenia i interfejsy</span><span class="sxs-lookup"><span data-stu-id="aefc0-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="aefc0-157">Gdy jest skojarzony z określonego typu za pomocą znanego typu `KnownTypeAttribute` atrybutu, znany typ jest także powiązany z wszystkich typów pochodnych danego typu.</span><span class="sxs-lookup"><span data-stu-id="aefc0-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="aefc0-158">Na przykład zobacz następujący kod.</span><span class="sxs-lookup"><span data-stu-id="aefc0-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="aefc0-159">`DoubleDrawing` Nie wymaga klasy `KnownTypeAttribute` atrybutu `Square` i `Circle` w `AdditionalShape` pola, ponieważ klasa podstawowa (`Drawing`) ma już te atrybuty stosowane.</span><span class="sxs-lookup"><span data-stu-id="aefc0-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="aefc0-160">Znanych typów może być skojarzony tylko z klas i struktur, nie interfejsy.</span><span class="sxs-lookup"><span data-stu-id="aefc0-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="aefc0-161">Znane typy przy użyciu Otwórz metody ogólne</span><span class="sxs-lookup"><span data-stu-id="aefc0-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="aefc0-162">Może być konieczne dodanie typem ogólnym jako znanego typu.</span><span class="sxs-lookup"><span data-stu-id="aefc0-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="aefc0-163">Jednak to otwarty typ ogólny nie mogą być przekazywane jako parametr `KnownTypeAttribute` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="aefc0-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="aefc0-164">Ten problem można rozwiązać przy użyciu alternatywny mechanizm: napisanie metody, która zwraca listę typów do dodania do kolekcji znanych typów.</span><span class="sxs-lookup"><span data-stu-id="aefc0-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="aefc0-165">Nazwa metody jest następnie określony jako argument będący ciągiem `KnownTypeAttribute` atrybutu z powodu pewne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="aefc0-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="aefc0-166">Metoda musi istnieć w typie, do którego `KnownTypeAttribute` atrybut jest stosowany, musi być statyczna, musisz zaakceptować bez parametrów i musi zwracać obiekt, który można przypisać do <xref:System.Collections.IEnumerable> z <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="aefc0-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="aefc0-167">Nie można łączyć `KnownTypeAttribute` atrybutu z nazwą metody i `KnownTypeAttribute` atrybuty z typami rzeczywistymi do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="aefc0-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="aefc0-168">Ponadto nie można zastosować więcej niż jeden `KnownTypeAttribute` nazwą metody do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="aefc0-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="aefc0-169">Zobacz następujące klasy.</span><span class="sxs-lookup"><span data-stu-id="aefc0-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="aefc0-170">`theDrawing` Pole zawiera wystąpień klasy generycznej `ColorDrawing` i klasy ogólnej `BlackAndWhiteDrawing`, które dziedziczą z klasy ogólnej `Drawing`.</span><span class="sxs-lookup"><span data-stu-id="aefc0-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="aefc0-171">Zwykle oba muszą zostać dodane do znanych typów, ale następujący ciąg nie jest prawidłową składnię dla atrybutów.</span><span class="sxs-lookup"><span data-stu-id="aefc0-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 <span data-ttu-id="aefc0-172">W związku z tym należy utworzyć metody w celu te typy zwracane.</span><span class="sxs-lookup"><span data-stu-id="aefc0-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="aefc0-173">Prawidłowy sposób można zapisać tego typu, następnie jest wyświetlany w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="aefc0-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="aefc0-174">Dodatkowe sposoby dodawania znanych typów</span><span class="sxs-lookup"><span data-stu-id="aefc0-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="aefc0-175">Ponadto można dodać za pomocą pliku konfiguracji znanych typów.</span><span class="sxs-lookup"><span data-stu-id="aefc0-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="aefc0-176">Jest to przydatne, gdy nie kontroli typ, który wymaga znanych typów dla odpowiednich deserializacji, takich jak przy użyciu innej firmy podczas wpisywania bibliotek z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aefc0-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
 <span data-ttu-id="aefc0-177">Następujący plik konfiguracji pokazano, jak określić znanego typu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="aefc0-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 <span data-ttu-id="aefc0-178">W tej konfiguracji pliku typu kontraktu danych o nazwie `MyCompany.Library.Shape` jest zadeklarowana, aby mieć `MyCompany.Library.Circle` jako znanego typu.</span><span class="sxs-lookup"><span data-stu-id="aefc0-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefc0-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aefc0-179">See Also</span></span>  
 <xref:System.Runtime.Serialization.KnownTypeAttribute>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Object>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>  
 [<span data-ttu-id="aefc0-180">Znane typy</span><span class="sxs-lookup"><span data-stu-id="aefc0-180">Known Types</span></span>](../../../../docs/framework/wcf/samples/known-types.md)  
 [<span data-ttu-id="aefc0-181">Równoważność kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="aefc0-181">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [<span data-ttu-id="aefc0-182">Projektowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="aefc0-182">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
