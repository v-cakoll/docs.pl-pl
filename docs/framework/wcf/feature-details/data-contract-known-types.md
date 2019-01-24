---
title: Znane typy kontraktów danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: d215d4b8adcf3e4892c00be1629f92b657496780
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705313"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="cdd3c-102">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="cdd3c-102">Data Contract Known Types</span></span>
<span data-ttu-id="cdd3c-103"><xref:System.Runtime.Serialization.KnownTypeAttribute> Klasy pozwala na określenie z wyprzedzeniem, typy, które należy wziąć pod uwagę podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="cdd3c-104">Aby uzyskać przykład pracy, zobacz [znane typy](../../../../docs/framework/wcf/samples/known-types.md) przykład.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-104">For a working example, see the [Known Types](../../../../docs/framework/wcf/samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="cdd3c-105">Zwykle podczas przekazywania parametrów i zwracanych wartości między klientem a usługą, oba punkty końcowe współdziel kontraktów danych danych przekazywanych.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="cdd3c-106">Jednak to nie jest wymagane w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="cdd3c-106">However, this is not the case in the following circumstances:</span></span>  
  
-   <span data-ttu-id="cdd3c-107">Kontrakt przesłanych danych jest tworzony na podstawie umowy oczekiwanych danych.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-107">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="cdd3c-108">Aby uzyskać więcej informacji, zobacz sekcję dotyczącą dziedziczenie w [równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span><span class="sxs-lookup"><span data-stu-id="cdd3c-108">For more information, see the section about inheritance in [Data Contract Equivalence](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span></span> <span data-ttu-id="cdd3c-109">W takim przypadku przesyłanych danych ma te same dane Umowę zgodnie z oczekiwaniami, odbieranie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
-   <span data-ttu-id="cdd3c-110">Deklarowany typ informacji przekazywanych jest interfejs, w przeciwieństwie do klasy, struktury lub wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="cdd3c-111">W związku z tym go nie może być znane z wyprzedzeniem typu czy implementuje interfejs są faktycznie przesyłane i w związku z tym, odbieranie punktu końcowego ustalić wcześniej kontraktu danych dla przesyłanych danych.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
-   <span data-ttu-id="cdd3c-112">Deklarowany typ informacji przekazywanych jest <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="cdd3c-113">Ponieważ każdy typ dziedziczy z <xref:System.Object>i go nie może być znane z wyprzedzeniem typy są faktycznie przesyłane, odbieranie punkt końcowy nie może ustalić z wyprzedzeniem kontraktu danych dla przesyłanych danych.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="cdd3c-114">To jest szczególnym przypadkiem pierwszego elementu: Co kontraktu danych pochodzi z domyślnej umowy puste dane, który jest generowany dla <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
-   <span data-ttu-id="cdd3c-115">Niektóre typy, które obejmują [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, mieć elementy członkowskie, które należą do jednej z trzech powyższych kategorii.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-115">Some types, which include [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="cdd3c-116">Na przykład <xref:System.Collections.Hashtable> używa <xref:System.Object> przechowywanie rzeczywistych obiektów w tablicy skrótów.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="cdd3c-117">Podczas serializacji tych typów, po stronie odbierającej nie może ustalić z wyprzedzeniem kontraktu danych dla tych członków.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="cdd3c-118">Klasa KnownTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="cdd3c-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="cdd3c-119">Dane odebrane na odbieranie punktu końcowego, środowisko wykonawcze programu WCF próbuje zdeserializowanie danych do wystąpienia typu wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="cdd3c-119">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="cdd3c-120">Typ, który zostanie uruchomiony do deserializacji jest wybierany sprawdzając pierwszego komunikatu przychodzącego do ustalenia danych umowę które treści wiadomości są zgodne.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="cdd3c-121">Następnie aparat deserializacji próbuje odnaleźć typu CLR, który implementuje kontraktu danych, zgodny z treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="cdd3c-122">Zestaw typów Release candidate, które umożliwiają aparatu deserializacji w trakcie tego procesu jest określany jako zestaw Deserializator "znanych typów."</span><span class="sxs-lookup"><span data-stu-id="cdd3c-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="cdd3c-123">Jednym ze sposobów, aby umożliwić aparatu deserializacji wiedzieć o typie jest przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="cdd3c-124">Nie można zastosować atrybut do poszczególnych elementów członkowskich danych, tylko typy kontraktu danych całego.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="cdd3c-125">Atrybut jest stosowany do *typu zewnętrznego* , może być klasą lub strukturą.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="cdd3c-126">W jej najprostsze użycie stosowanie atrybutu określa typ jako "znanych type".</span><span class="sxs-lookup"><span data-stu-id="cdd3c-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="cdd3c-127">Powoduje to, że znany typ jako część zestawu znanych typów, zawsze wtedy, gdy obiekt typu zewnętrznego lub wykonać deserializacji dowolny obiekt określony przez jego członków.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="cdd3c-128">Więcej niż jeden <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybut można stosować do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="cdd3c-129">Znane typy i elementy podstawowe</span><span class="sxs-lookup"><span data-stu-id="cdd3c-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="cdd3c-130">Typy pierwotne, a także niektórych typów traktowane jako elementy podstawowe (na przykład <xref:System.DateTime> i <xref:System.Xml.XmlElement>) są zawsze "Nieznany" i nigdy nie muszą być dodane za pomocą tego mechanizmu.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="cdd3c-131">Jednak tablic prymitywnych typów muszą być dodane jawnie.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="cdd3c-132">Większość kolekcji są uważane za równoważne do tablic.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="cdd3c-133">(Inne niż ogólne kolekcje są uważane za równoważne do tablic <xref:System.Object>).</span><span class="sxs-lookup"><span data-stu-id="cdd3c-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="cdd3c-134">Na przykład przy użyciu podstawowych, pierwotnych tablice i kolekcje pierwotnych, zobacz przykład 4.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdd3c-135">W przeciwieństwie do innych typów pierwotnych <xref:System.DateTimeOffset> struktura nie jest znany typ domyślnie, dlatego należy ręcznie dodać do listy znanych typów.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cdd3c-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cdd3c-136">Examples</span></span>  
 <span data-ttu-id="cdd3c-137">W poniższych przykładach pokazano <xref:System.Runtime.Serialization.KnownTypeAttribute> klasy w użyciu.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="cdd3c-138">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="cdd3c-138">Example 1</span></span>  
 <span data-ttu-id="cdd3c-139">Istnieją trzy klasy przy użyciu relacji dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="cdd3c-140">Następujące `CompanyLogo` klasy może być Zserializowany, ale nie można zdeserializować, jeśli `ShapeOfLogo` element członkowski jest ustawiany na `CircleType` lub `TriangleType` obiektu, ponieważ aparat deserializacji nie rozpoznaje wszystkie typy z nazw kontraktu danych " Koło"lub"Trójkąt".</span><span class="sxs-lookup"><span data-stu-id="cdd3c-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="cdd3c-141">Poprawny sposób zapisu `CompanyLogo` typu jest wyświetlana w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="cdd3c-142">Zawsze, gdy typu zewnętrznego `CompanyLogo2` jest przeprowadzona, aparat deserializacji wie o `CircleType` i `TriangleType` i dlatego jest w stanie znaleźć pasujące typy kontraktów danych "Koło" i "Trójkąt".</span><span class="sxs-lookup"><span data-stu-id="cdd3c-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="cdd3c-143">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="cdd3c-143">Example 2</span></span>  
 <span data-ttu-id="cdd3c-144">W poniższym przykładzie mimo że zarówno `CustomerTypeA` i `CustomerTypeB` mają `Customer` kontraktu danych, wystąpienie `CustomerTypeB` jest tworzony w każdym przypadku, gdy `PurchaseOrder` jest przeprowadzona, ponieważ tylko `CustomerTypeB` znanego Aparat deserializacji.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="cdd3c-145">Przykład 3</span><span class="sxs-lookup"><span data-stu-id="cdd3c-145">Example 3</span></span>  
 <span data-ttu-id="cdd3c-146">W poniższym przykładzie <xref:System.Collections.Hashtable> jej zawartość są przechowywane wewnętrznie jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="cdd3c-147">Aby pomyślnie zdeserializowanie tablicy skrótów, aparat deserializacji trzeba znać zestaw możliwych typów, które mogą wystąpić, istnieje.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="cdd3c-148">W tym przypadku wiemy z wyprzedzeniem tylko `Book` i `Magazine` obiekty są przechowywane w `Catalog`, więc te są dodawane przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="cdd3c-149">Przykład 4</span><span class="sxs-lookup"><span data-stu-id="cdd3c-149">Example 4</span></span>  
 <span data-ttu-id="cdd3c-150">W poniższym przykładzie kontraktu danych przechowuje liczbę i operacji do wykonania na liczbę.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="cdd3c-151">`Numbers` Element członkowski danych może być liczbą całkowitą, tablicy liczb całkowitych, lub <xref:System.Collections.Generic.List%601> zawierający liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="cdd3c-152">Ta opcja zadziała tylko po stronie klienta Jeśli narzędzia SVCUTIL. Plik EXE jest używany do generowania serwera proxy usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="cdd3c-153">NARZĘDZIA SVCUTIL. Plik EXE pobiera metadane z usługi, w tym wszystkie znane typy.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="cdd3c-154">Bez tych informacji klienta nie będzie można wykonać deserializacji typów.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="cdd3c-155">Jest to kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="cdd3c-156">Znanych typów, dziedziczenie i interfejsy</span><span class="sxs-lookup"><span data-stu-id="cdd3c-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="cdd3c-157">Jeśli znany typ jest skojarzony z określonego typu, w którym używana jest `KnownTypeAttribute` , znany typ jest również skojarzony z wszystkich typów pochodnych tego typu.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="cdd3c-158">Zobacz na przykład, poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="cdd3c-159">`DoubleDrawing` Klasy nie wymaga `KnownTypeAttribute` atrybutu `Square` i `Circle` w `AdditionalShape` pola, ponieważ klasa bazowa (`Drawing`) ma już te atrybuty zastosowane.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="cdd3c-160">Znane typy mogą zostać skojarzone tylko z klas i struktur, interfejsów nie.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="cdd3c-161">Znane typy, za pomocą otwartych metod ogólnych</span><span class="sxs-lookup"><span data-stu-id="cdd3c-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="cdd3c-162">Może być konieczne dodanie typem ogólnym jako znanego typu.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="cdd3c-163">Jednak to otwarty typ ogólny nie można przekazać jako parametru `KnownTypeAttribute` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="cdd3c-164">Ten problem można rozwiązać za pomocą alternatywny mechanizm: Napisanie metody, która zwraca listę typów, aby dodać do kolekcji znanych typów.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="cdd3c-165">Nazwa metody jest następnie określony jako argument ciągu `KnownTypeAttribute` atrybut ze względu na pewne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="cdd3c-166">Metoda musi istnieć na typ, do którego `KnownTypeAttribute` atrybut jest stosowany, muszą być statyczne, należy zaakceptować żadnych parametrów i musi zwracać obiekt, który można przypisać do <xref:System.Collections.IEnumerable> z <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="cdd3c-167">Nie można łączyć `KnownTypeAttribute` atrybutu o nazwie metody i `KnownTypeAttribute` atrybuty z typami rzeczywistymi do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="cdd3c-168">Ponadto nie można zastosować więcej niż jedną `KnownTypeAttribute` nazwą metody do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="cdd3c-169">Zobacz następujące klasy.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="cdd3c-170">`theDrawing` Pole zawiera wystąpienia klasy generycznej `ColorDrawing` i klasę ogólną `BlackAndWhiteDrawing`, które dziedziczą z klasy rodzajowej `Drawing`.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="cdd3c-171">Normalnie oba muszą zostać dodane do znanych typów, ale poniżej nie jest prawidłową składnię dla atrybutów.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
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
  
 <span data-ttu-id="cdd3c-172">W związku z tym metoda musi zostać utworzona do tych typów zwracanych.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="cdd3c-173">Poprawny sposób pisania tego typu, następnie jest wyświetlany w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="cdd3c-174">Dodatkowe sposoby dodawania znane typy</span><span class="sxs-lookup"><span data-stu-id="cdd3c-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="cdd3c-175">Ponadto można dodać znanych typów za pomocą pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="cdd3c-176">Jest to przydatne, gdy nie mają kontroli nad typ, który wymaga znanych typów do odpowiednich deserializacji, np. gdy przy użyciu innych firm wpisz biblioteki za pomocą programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="cdd3c-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="cdd3c-177">Następujący plik konfiguracji pokazuje sposób określania znanego typu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="cdd3c-178">W tej konfiguracji pliku typu kontraktu danych, nazywane `MyCompany.Library.Shape` jest zadeklarowany ma `MyCompany.Library.Circle` jako znanego typu.</span><span class="sxs-lookup"><span data-stu-id="cdd3c-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd3c-179">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdd3c-179">See also</span></span>
- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="cdd3c-180">Znane typy</span><span class="sxs-lookup"><span data-stu-id="cdd3c-180">Known Types</span></span>](../../../../docs/framework/wcf/samples/known-types.md)
- [<span data-ttu-id="cdd3c-181">Równoważność kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="cdd3c-181">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="cdd3c-182">Projektowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="cdd3c-182">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
