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
ms.openlocfilehash: b7d78def4d656dea59af5400c7ed7deeef28cd0c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597452"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="0ec16-102">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="0ec16-102">Data Contract Known Types</span></span>
<span data-ttu-id="0ec16-103"><xref:System.Runtime.Serialization.KnownTypeAttribute>Klasa pozwala określić z wyprzedzeniem typy, które powinny być brane pod uwagę podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="0ec16-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="0ec16-104">Aby zapoznać się z przykładem roboczym, zobacz przykład [znanych typów](../samples/known-types.md) .</span><span class="sxs-lookup"><span data-stu-id="0ec16-104">For a working example, see the [Known Types](../samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="0ec16-105">Zwykle podczas przekazywania parametrów i zwracanych wartości między klientem a usługą oba punkty końcowe współdzielą wszystkie Kontrakty danych do przesłania.</span><span class="sxs-lookup"><span data-stu-id="0ec16-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="0ec16-106">Nie dotyczy to jednak następujących sytuacji:</span><span class="sxs-lookup"><span data-stu-id="0ec16-106">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="0ec16-107">Kontrakt wysłanych danych pochodzi od oczekiwanego kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="0ec16-107">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="0ec16-108">Aby uzyskać więcej informacji, zapoznaj się z sekcją dotyczącej dziedziczenia w obszarze [równoważności kontraktu danych](data-contract-equivalence.md).</span><span class="sxs-lookup"><span data-stu-id="0ec16-108">For more information, see the section about inheritance in [Data Contract Equivalence](data-contract-equivalence.md)).</span></span> <span data-ttu-id="0ec16-109">W takim przypadku przesyłane dane nie mają tego samego kontraktu danych zgodnie z oczekiwaniami w punkcie końcowym odbioru.</span><span class="sxs-lookup"><span data-stu-id="0ec16-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="0ec16-110">Zadeklarowany typ dla przekazywanych informacji jest interfejsem, a nie z klasą, strukturą lub wyliczeniem.</span><span class="sxs-lookup"><span data-stu-id="0ec16-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="0ec16-111">W związku z tym nie może być znany z wyprzedzeniem, który typ implementujący interfejs jest faktycznie wysyłany i dlatego punkt końcowy odbiorcy nie może określić z wyprzedzeniem kontraktu danych dla przesyłanych danych.</span><span class="sxs-lookup"><span data-stu-id="0ec16-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="0ec16-112">Zadeklarowany typ dla przekazywanych informacji to <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="0ec16-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="0ec16-113">Ponieważ każdy typ dziedziczy z <xref:System.Object> i nie może być znany z wyprzedzeniem, który jest faktycznie wysyłany, punkt końcowy odbiorcy nie może określić z wyprzedzeniem kontraktu danych dla przesyłanych danych.</span><span class="sxs-lookup"><span data-stu-id="0ec16-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="0ec16-114">Jest to specjalny przypadek pierwszego elementu: każdy kontrakt danych pochodzi z domyślnego, pustego kontraktu danych wygenerowanego dla <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="0ec16-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="0ec16-115">Niektóre typy, które obejmują .NET Framework typy, mają składowe, które znajdują się w jednej z powyższych trzech kategorii.</span><span class="sxs-lookup"><span data-stu-id="0ec16-115">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="0ec16-116">Na przykład program <xref:System.Collections.Hashtable> używa <xref:System.Object> do przechowywania rzeczywistych obiektów w tabeli skrótów.</span><span class="sxs-lookup"><span data-stu-id="0ec16-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="0ec16-117">Podczas serializacji tych typów Strona otrzymująca nie może określić z wyprzedzeniem kontraktu danych dla tych członków.</span><span class="sxs-lookup"><span data-stu-id="0ec16-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="0ec16-118">Klasa KnownTypeattribute</span><span class="sxs-lookup"><span data-stu-id="0ec16-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="0ec16-119">Gdy dane docierają do odbiorczego punktu końcowego, środowisko uruchomieniowe WCF próbuje zdeserializować dane do wystąpienia aparatu plików wykonywalnych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="0ec16-119">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="0ec16-120">Typ, który jest skonkretyzowany dla deserializacji jest wybierany przez pierwsze Inspekcja komunikatu przychodzącego, aby określić kontrakt danych, do którego zawartość wiadomości jest zgodna.</span><span class="sxs-lookup"><span data-stu-id="0ec16-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="0ec16-121">Aparat deserializacji próbuje znaleźć typ CLR, który implementuje kontrakt danych zgodny z zawartością wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0ec16-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="0ec16-122">Zestaw typów kandydujących, które mogą być używane przez aparat deserializacji w trakcie tego procesu, jest nazywany zestawem "znanych typów".</span><span class="sxs-lookup"><span data-stu-id="0ec16-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="0ec16-123">Jednym ze sposobów na umożliwienie aparatowi deserializacji informacji o typie jest użycie <xref:System.Runtime.Serialization.KnownTypeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0ec16-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="0ec16-124">Nie można zastosować atrybutu do poszczególnych składowych danych, tylko do typów kontraktu danych całych.</span><span class="sxs-lookup"><span data-stu-id="0ec16-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="0ec16-125">Ten atrybut jest stosowany do *typu zewnętrznego* , który może być klasą lub strukturą.</span><span class="sxs-lookup"><span data-stu-id="0ec16-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="0ec16-126">W najbardziej podstawowym użyciu, zastosowanie atrybutu określa typ jako "znany typ".</span><span class="sxs-lookup"><span data-stu-id="0ec16-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="0ec16-127">Powoduje to, że znany typ jest częścią zestawu znanych typów za każdym razem, gdy obiekt typu zewnętrznego lub dowolnego obiektu, do którego odwołuje się jego składowe, jest deserializowany.</span><span class="sxs-lookup"><span data-stu-id="0ec16-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="0ec16-128"><xref:System.Runtime.Serialization.KnownTypeAttribute>Do tego samego typu można zastosować więcej niż jeden atrybut.</span><span class="sxs-lookup"><span data-stu-id="0ec16-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="0ec16-129">Znane typy i elementy podstawowe</span><span class="sxs-lookup"><span data-stu-id="0ec16-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="0ec16-130">Typy pierwotne, a także niektóre typy traktowane jako elementy pierwotne (na przykład <xref:System.DateTime> i <xref:System.Xml.XmlElement> ) są zawsze "znane" i nigdy nie muszą być dodawane przez ten mechanizm.</span><span class="sxs-lookup"><span data-stu-id="0ec16-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="0ec16-131">Jednakże tablice typów pierwotnych muszą być dodawane jawnie.</span><span class="sxs-lookup"><span data-stu-id="0ec16-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="0ec16-132">Większość kolekcji jest traktowana jako odpowiednik tablic.</span><span class="sxs-lookup"><span data-stu-id="0ec16-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="0ec16-133">(Kolekcje inne niż ogólne są uważane za równoważne tablicom <xref:System.Object> ).</span><span class="sxs-lookup"><span data-stu-id="0ec16-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="0ec16-134">Aby zapoznać się z przykładem typów pierwotnych, tablic podstawowych i kolekcji pierwotnych, zobacz przykład 4.</span><span class="sxs-lookup"><span data-stu-id="0ec16-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ec16-135">W przeciwieństwie do innych typów pierwotnych, <xref:System.DateTimeOffset> Struktura nie jest typem znanym domyślnie, więc należy ją dodać ręcznie do listy znanych typów.</span><span class="sxs-lookup"><span data-stu-id="0ec16-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0ec16-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="0ec16-136">Examples</span></span>  
 <span data-ttu-id="0ec16-137">W poniższych przykładach przedstawiono <xref:System.Runtime.Serialization.KnownTypeAttribute> klasę używaną.</span><span class="sxs-lookup"><span data-stu-id="0ec16-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="0ec16-138">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="0ec16-138">Example 1</span></span>  
 <span data-ttu-id="0ec16-139">Istnieją trzy klasy z relacją dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="0ec16-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="0ec16-140">Następująca `CompanyLogo` Klasa może być serializowana, ale nie można jej zdeserializować, jeśli `ShapeOfLogo` element członkowski jest ustawiony na albo `CircleType` `TriangleType` obiekt, ponieważ aparat deserializacji nie rozpoznaje żadnych typów z nazwami kontraktu danych "Circle" lub "trójkąt".</span><span class="sxs-lookup"><span data-stu-id="0ec16-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="0ec16-141">Poprawna Metoda pisania `CompanyLogo` typu jest pokazana w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0ec16-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="0ec16-142">Za każdym razem, gdy typ zewnętrzny `CompanyLogo2` jest deserializowany, aparat deserializacji wie o `CircleType` i `TriangleType` i, w związku z tym, może znaleźć pasujące typy kontraktów danych "Circle" i "Trójkąty".</span><span class="sxs-lookup"><span data-stu-id="0ec16-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="0ec16-143">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="0ec16-143">Example 2</span></span>  
 <span data-ttu-id="0ec16-144">W poniższym przykładzie, mimo że oba `CustomerTypeA` i `CustomerTypeB` mają `Customer` umowę danych, wystąpienie `CustomerTypeB` jest tworzone za każdym razem `PurchaseOrder` , gdy jest deserializowany, ponieważ `CustomerTypeB` jest znane tylko dla aparatu deserializacji.</span><span class="sxs-lookup"><span data-stu-id="0ec16-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="0ec16-145">Przykład 3</span><span class="sxs-lookup"><span data-stu-id="0ec16-145">Example 3</span></span>  
 <span data-ttu-id="0ec16-146">W poniższym przykładzie <xref:System.Collections.Hashtable> zawartość jest przechowywana wewnętrznie jako <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="0ec16-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="0ec16-147">Aby pomyślnie deserializować tablicę skrótów, aparat deserializacji musi znać zestaw możliwych typów, które mogą wystąpić w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="0ec16-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="0ec16-148">W takim przypadku wiemy, że tylko `Book` `Magazine` obiekty są przechowywane w `Catalog` , dlatego są one dodawane przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0ec16-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="0ec16-149">Przykład 4</span><span class="sxs-lookup"><span data-stu-id="0ec16-149">Example 4</span></span>  
 <span data-ttu-id="0ec16-150">W poniższym przykładzie kontrakt danych przechowuje liczbę i operację do wykonania na numerze.</span><span class="sxs-lookup"><span data-stu-id="0ec16-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="0ec16-151">`Numbers`Składowa danych może być liczbą całkowitą, tablicą liczb całkowitych lub zawierającą <xref:System.Collections.Generic.List%601> liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="0ec16-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="0ec16-152">Ta wartość będzie działała tylko po stronie klienta, jeśli SVCUTIL. Plik EXE jest używany do generowania serwera proxy WCF.</span><span class="sxs-lookup"><span data-stu-id="0ec16-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="0ec16-153">Svcutil. EXE pobiera metadane z usługi, w tym wszystkie znane typy.</span><span class="sxs-lookup"><span data-stu-id="0ec16-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="0ec16-154">Bez tych informacji klient nie będzie mógł deserializować typów.</span><span class="sxs-lookup"><span data-stu-id="0ec16-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="0ec16-155">Jest to kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0ec16-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="0ec16-156">Znane typy, dziedziczenie i interfejsy</span><span class="sxs-lookup"><span data-stu-id="0ec16-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="0ec16-157">Gdy znany typ jest skojarzony z określonym typem przy użyciu `KnownTypeAttribute` atrybutu, znany typ jest również skojarzony ze wszystkimi typami pochodnymi tego typu.</span><span class="sxs-lookup"><span data-stu-id="0ec16-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="0ec16-158">Na przykład zapoznaj się z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="0ec16-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="0ec16-159">`DoubleDrawing`Klasa nie wymaga, `KnownTypeAttribute` Aby atrybut był używany `Square` i `Circle` w `AdditionalShape` polu, ponieważ klasa bazowa ( `Drawing` ) ma już zastosowane te atrybuty.</span><span class="sxs-lookup"><span data-stu-id="0ec16-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="0ec16-160">Znane typy można kojarzyć tylko z klasami i strukturami, a nie interfejsami.</span><span class="sxs-lookup"><span data-stu-id="0ec16-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="0ec16-161">Znane typy używające otwartych metod ogólnych</span><span class="sxs-lookup"><span data-stu-id="0ec16-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="0ec16-162">Może być konieczne dodanie typu ogólnego jako znanego typu.</span><span class="sxs-lookup"><span data-stu-id="0ec16-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="0ec16-163">Jednak otwarty typ generyczny nie może być przekazywać jako parametr do `KnownTypeAttribute` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0ec16-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="0ec16-164">Ten problem można rozwiązać przy użyciu alternatywnego mechanizmu: Napisz metodę, która zwraca listę typów do dodania do kolekcji znanych typów.</span><span class="sxs-lookup"><span data-stu-id="0ec16-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="0ec16-165">Nazwa metody jest następnie określona jako argument ciągu dla `KnownTypeAttribute` atrybutu z powodu pewnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="0ec16-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="0ec16-166">Metoda musi istnieć w typie, do którego `KnownTypeAttribute` zastosowano atrybut, musi być statyczna, nie może akceptować parametrów i musi zwracać obiekt, do którego można przypisać <xref:System.Collections.IEnumerable> <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="0ec16-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="0ec16-167">Nie można połączyć `KnownTypeAttribute` atrybutu z nazwą metody i `KnownTypeAttribute` atrybutami o rzeczywistych typach tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="0ec16-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="0ec16-168">Ponadto nie można zastosować więcej niż jednego `KnownTypeAttribute` z nazwą metody do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="0ec16-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="0ec16-169">Zapoznaj się z następującą klasą.</span><span class="sxs-lookup"><span data-stu-id="0ec16-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="0ec16-170">`theDrawing`Pole zawiera wystąpienia klasy generycznej `ColorDrawing` i klasy generycznej `BlackAndWhiteDrawing` , które dziedziczą z klasy generycznej `Drawing` .</span><span class="sxs-lookup"><span data-stu-id="0ec16-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="0ec16-171">Zwykle obydwie muszą być dodawane do znanych typów, ale Poniższa składnia nie jest prawidłową składnią dla atrybutów.</span><span class="sxs-lookup"><span data-stu-id="0ec16-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
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
  
 <span data-ttu-id="0ec16-172">W tym celu należy utworzyć metodę, aby zwracała te typy.</span><span class="sxs-lookup"><span data-stu-id="0ec16-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="0ec16-173">Prawidłowy sposób zapisu tego typu, a następnie pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0ec16-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="0ec16-174">Dodatkowe sposoby dodawania znanych typów</span><span class="sxs-lookup"><span data-stu-id="0ec16-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="0ec16-175">Ponadto znane typy można dodawać za pomocą pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0ec16-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="0ec16-176">Jest to przydatne, gdy nie kontrolujesz typu wymagającego znanych typów do właściwej deserializacji, na przykład w przypadku używania bibliotek typów innych firm z Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0ec16-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="0ec16-177">Poniższy plik konfiguracji przedstawia sposób określenia znanego typu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0ec16-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="0ec16-178">W poprzednim pliku konfiguracji typ kontraktu danych o nazwie `MyCompany.Library.Shape` jest zadeklarowany `MyCompany.Library.Circle` jako znany typ.</span><span class="sxs-lookup"><span data-stu-id="0ec16-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ec16-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ec16-179">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="0ec16-180">Znane typy</span><span class="sxs-lookup"><span data-stu-id="0ec16-180">Known Types</span></span>](../samples/known-types.md)
- [<span data-ttu-id="0ec16-181">Równoważność kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="0ec16-181">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="0ec16-182">Projektowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="0ec16-182">Designing Service Contracts</span></span>](../designing-service-contracts.md)
