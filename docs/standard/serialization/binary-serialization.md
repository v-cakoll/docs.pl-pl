---
title: Serializacja binarna
ms.date: 08/11/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
caps.latest.revision: "5"
author: ViktorHofer
ms.author: mairaw
ms.openlocfilehash: 74ee4e21934c1e4f3fd008664b1315429dc47b37
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="binary-serialization"></a><span data-ttu-id="67a89-102">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="67a89-102">Binary serialization</span></span>

<span data-ttu-id="67a89-103">Serializacja mogą być definiowane jako proces przechowywania stanu obiektu na nośniku.</span><span class="sxs-lookup"><span data-stu-id="67a89-103">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="67a89-104">W trakcie tego procesu publiczny i prywatny pola obiektu oraz nazwę klasy, łącznie z zestawu zawierającego klasy, są konwertowane na strumień bajtów, które są następnie zapisywane do strumienia danych.</span><span class="sxs-lookup"><span data-stu-id="67a89-104">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="67a89-105">Gdy obiekt jest następnie przeprowadzona, dokładną oryginalnego obiektu zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="67a89-105">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="67a89-106">Podczas implementowania mechanizmu serializacji w środowisku zorientowane obiektowo, konieczne będzie wprowadzenie numeru kompromisów między łatwość użycia i elastyczność.</span><span class="sxs-lookup"><span data-stu-id="67a89-106">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="67a89-107">Ten proces można automatycznego w dużym stopniu, pod warunkiem, że podane są wystarczające kontrolę nad procesem.</span><span class="sxs-lookup"><span data-stu-id="67a89-107">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="67a89-108">Na przykład sytuacji mogą wystąpić podczas gdzie proste serializacji binarnej jest niewystarczająca lub może być powód, aby określić pola, które w klasie muszą być serializowane.</span><span class="sxs-lookup"><span data-stu-id="67a89-108">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="67a89-109">W poniższych sekcjach zbadać mechanizmu serializacji niezawodne dostarczony wraz z programem .NET i zaznacz wiele ważnych funkcji, które umożliwiają dostosowanie procesu do własnych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="67a89-109">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="67a89-110">Stan UTF-8 lub UTF-7 kodowany obiektu nie jest zachowana, jeśli obiekt jest serializacji i deserializacji za pomocą różnych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67a89-110">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="67a89-111">Jak rodzaj serializacji binarnej pozwala na modyfikację prywatne elementy członkowskie wewnątrz i dlatego zmiany stanu tego obiektu, zaleca się innych platform serializacji jak JSON.NET, które działają w publicznej powierzchni interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="67a89-111">As the nature of binary serialization allows the modification of private members inside an object and therefore changing the state of it, other serialization frameworks like JSON.NET which operate on the public API surface are recommended.</span></span>

## <a name="binary-serialization-in-net-core"></a><span data-ttu-id="67a89-112">Serializacja binarna w .NET Core</span><span class="sxs-lookup"><span data-stu-id="67a89-112">Binary serialization in .NET Core</span></span>

<span data-ttu-id="67a89-113">Oprogramowanie .NET core obsługuje serializacji binarnej z podzbioru typów.</span><span class="sxs-lookup"><span data-stu-id="67a89-113">.NET Core supports binary serialization with a subset of types.</span></span> <span data-ttu-id="67a89-114">Można wyświetlić listę obsługiwanych typów w [sekcji typów możliwych do serializacji](#serializable-types).</span><span class="sxs-lookup"><span data-stu-id="67a89-114">You can see the list of supported types in the [Serializable types section](#serializable-types).</span></span> <span data-ttu-id="67a89-115">Zestaw określonych typów zapewniona jest możliwy do serializacji między .NET Framework 4.5.1 i nowszych wersjach i .NET Core 2.0 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="67a89-115">The defined set of types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="67a89-116">Inne implementacje .NET, takie jak Mono, oficjalnie nie są obsługiwane, ale również powinny działać.</span><span class="sxs-lookup"><span data-stu-id="67a89-116">Other .NET implementations, such as Mono, aren't officially supported but should also be working.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="67a89-117">Typów możliwych do serializacji</span><span class="sxs-lookup"><span data-stu-id="67a89-117">Serializable types</span></span>

- <xref:System.AggregateException?displayProperty=nameWithType>   
- <xref:System.Array?displayProperty=nameWithType>   
- <xref:System.ArraySegment%601?displayProperty=nameWithType>   
- <xref:System.Attribute?displayProperty=nameWithType>   
- <xref:System.Boolean?displayProperty=nameWithType>   
- <xref:System.Byte?displayProperty=nameWithType>   
- <xref:System.Char?displayProperty=nameWithType>   
- <xref:System.Collections.ArrayList?displayProperty=nameWithType>   
- <xref:System.Collections.BitArray?displayProperty=nameWithType>   
- <xref:System.Collections.Comparer?displayProperty=nameWithType>   
- <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>   
- <xref:System.Collections.Hashtable?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.Queue?displayProperty=nameWithType>   
- <xref:System.Collections.SortedList?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Stack?displayProperty=nameWithType>   
- <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType>   
- <span data-ttu-id="67a89-118"><xref:System.DBNull?displayProperty=nameWithType>(dostępne w .NET Core pkt 2.0.2 i nowsze wersje)</span><span class="sxs-lookup"><span data-stu-id="67a89-118"><xref:System.DBNull?displayProperty=nameWithType> (available in .NET Core 2.0.2 and later versions)</span></span>   
- <xref:System.Data.DataSet?displayProperty=nameWithType>   
- <xref:System.Data.DataTable?displayProperty=nameWithType>   
- <xref:System.Data.PropertyCollection?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType>   
- <xref:System.DateTime?displayProperty=nameWithType>   
- <xref:System.DateTimeOffset?displayProperty=nameWithType>   
- <xref:System.Decimal?displayProperty=nameWithType>   
- <xref:System.Double?displayProperty=nameWithType>   
- <xref:System.Drawing.Color?displayProperty=nameWithType>   
- <xref:System.Drawing.Point?displayProperty=nameWithType>   
- <xref:System.Drawing.PointF?displayProperty=nameWithType>   
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>   
- <xref:System.Drawing.RectangleF?displayProperty=nameWithType>   
- <xref:System.Drawing.Size?displayProperty=nameWithType>   
- <xref:System.Drawing.SizeF?displayProperty=nameWithType>   
- <xref:System.Enum?displayProperty=nameWithType>   
- <xref:System.Exception?displayProperty=nameWithType>   
- <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>   
- <xref:System.Globalization.SortVersion?displayProperty=nameWithType>   
- <xref:System.Guid?displayProperty=nameWithType>   
- <xref:System.Int16?displayProperty=nameWithType>   
- <xref:System.Int32?displayProperty=nameWithType>   
- <xref:System.Int64?displayProperty=nameWithType>   
- <xref:System.IntPtr?displayProperty=nameWithType>   
- <xref:System.Net.Cookie?displayProperty=nameWithType>   
- <xref:System.Net.CookieCollection?displayProperty=nameWithType>   
- <xref:System.Net.CookieContainer?displayProperty=nameWithType>   
- <xref:System.Nullable%601?displayProperty=nameWithType>   
- <xref:System.Numerics.BigInteger?displayProperty=nameWithType>   
- <xref:System.Numerics.Complex?displayProperty=nameWithType>   
- <xref:System.Object?displayProperty=nameWithType>   
- <xref:System.SByte?displayProperty=nameWithType>   
- <xref:System.Single?displayProperty=nameWithType>   
- <xref:System.String?displayProperty=nameWithType>   
- <xref:System.StringComparer?displayProperty=nameWithType>   
- <xref:System.Text.StringBuilder?displayProperty=nameWithType>   
- <xref:System.TimeSpan?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType>   
- <xref:System.Tuple?displayProperty=nameWithType>   
- <xref:System.UInt16?displayProperty=nameWithType>   
- <xref:System.UInt32?displayProperty=nameWithType>   
- <xref:System.UInt64?displayProperty=nameWithType>   
- <xref:System.UIntPtr?displayProperty=nameWithType>   
- <xref:System.Uri?displayProperty=nameWithType>   
- <span data-ttu-id="67a89-119"><xref:System.ValueTuple?displayProperty=nameWithType>(nie można serializować w .NET Framework 4.7 i wcześniejsze wersje)</span><span class="sxs-lookup"><span data-stu-id="67a89-119"><xref:System.ValueTuple?displayProperty=nameWithType> (not serializable in .NET Framework 4.7 and earlier versions)</span></span>  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   

## <a name="in-this-section"></a><span data-ttu-id="67a89-120">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="67a89-120">In this section</span></span>

 [<span data-ttu-id="67a89-121">Pojęcia dotyczące serializacji</span><span class="sxs-lookup"><span data-stu-id="67a89-121">Serialization Concepts</span></span>](../../../docs/standard/serialization/serialization-concepts.md)  
 <span data-ttu-id="67a89-122">Opisano dwa scenariusze, w których serializacji jest użyteczny: gdy trwałych danych do magazynu i przekazywanie obiektów między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67a89-122">Discusses two scenarios where serialization is useful: when persisting data to storage and when passing objects across application domains.</span></span>  
  
 [<span data-ttu-id="67a89-123">Podstawowe serializacji</span><span class="sxs-lookup"><span data-stu-id="67a89-123">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 <span data-ttu-id="67a89-124">Opisuje sposób używania PLiku binarnego i SOAP elementy formatujące do wykonywania serializacji obiektów.</span><span class="sxs-lookup"><span data-stu-id="67a89-124">Describes how to use the binary and SOAP formatters to serialize objects.</span></span>  
  
 [<span data-ttu-id="67a89-125">Selektywne serializacji</span><span class="sxs-lookup"><span data-stu-id="67a89-125">Selective Serialization</span></span>](../../../docs/standard/serialization/selective-serialization.md)  
 <span data-ttu-id="67a89-126">Opisuje sposób zapobiegania serializacji niektórych składowych klasy.</span><span class="sxs-lookup"><span data-stu-id="67a89-126">Describes how to prevent some members of a class from being serialized.</span></span>  
  
 [<span data-ttu-id="67a89-127">Niestandardowej serializacji</span><span class="sxs-lookup"><span data-stu-id="67a89-127">Custom Serialization</span></span>](../../../docs/standard/serialization/custom-serialization.md)  
 <span data-ttu-id="67a89-128">Opisuje sposób dostosowywania serializacji dla klasy przy użyciu <xref:System.Runtime.Serialization.ISerializable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="67a89-128">Describes how to customize serialization for a class by using the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 [<span data-ttu-id="67a89-129">Kroki procesu serializacji</span><span class="sxs-lookup"><span data-stu-id="67a89-129">Steps in the Serialization Process</span></span>](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 <span data-ttu-id="67a89-130">Opisuje kurs akcji serializacji przyjmuje, gdy <xref:System.Runtime.Serialization.Formatter.Serialize%2A> metoda jest wywoływana w elementu formatującego.</span><span class="sxs-lookup"><span data-stu-id="67a89-130">Describes the course of action serialization takes when the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a formatter.</span></span>  
  
 [<span data-ttu-id="67a89-131">Serializacji z tolerancją dla wersji</span><span class="sxs-lookup"><span data-stu-id="67a89-131">Version Tolerant Serialization</span></span>](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 <span data-ttu-id="67a89-132">Wyjaśnia sposób tworzenia typów możliwych do serializacji, które mogą być modyfikowane w czasie bez powodowania aplikacjom zgłaszają wyjątki.</span><span class="sxs-lookup"><span data-stu-id="67a89-132">Explains how to create serializable types that can be modified over time without causing applications to throw exceptions.</span></span>  
  
 [<span data-ttu-id="67a89-133">Wytyczne serializacji</span><span class="sxs-lookup"><span data-stu-id="67a89-133">Serialization Guidelines</span></span>](../../../docs/standard/serialization/serialization-guidelines.md)  
 <span data-ttu-id="67a89-134">Zawiera ogólne zasady ustalania, kiedy można serializować obiektu.</span><span class="sxs-lookup"><span data-stu-id="67a89-134">Provides some general guidelines for deciding when to serialize an object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="67a89-135">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="67a89-135">Reference</span></span>  
 <xref:System.Runtime.Serialization>  
 <span data-ttu-id="67a89-136">Zawiera klasy, które mogą być używane do serializacji i deserializacji obiektów.</span><span class="sxs-lookup"><span data-stu-id="67a89-136">Contains classes that can be used for serializing and deserializing objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="67a89-137">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="67a89-137">Related sections</span></span>  
 [<span data-ttu-id="67a89-138">XML i serializacji SOAP</span><span class="sxs-lookup"><span data-stu-id="67a89-138">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 <span data-ttu-id="67a89-139">Opisuje mechanizm serializacji XML, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="67a89-139">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>  
  
 [<span data-ttu-id="67a89-140">Zabezpieczenia i serializacja</span><span class="sxs-lookup"><span data-stu-id="67a89-140">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)  
 <span data-ttu-id="67a89-141">Opisuje bezpiecznego wskazówek kodowania, które należy wykonać podczas pisania kodu, który będzie wykonywać serializacji.</span><span class="sxs-lookup"><span data-stu-id="67a89-141">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>  
  
 [<span data-ttu-id="67a89-142">Obiekty zdalnego</span><span class="sxs-lookup"><span data-stu-id="67a89-142">Remote Objects</span></span>](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 <span data-ttu-id="67a89-143">Opis różnych metod komunikacji dostępnych w programie .NET Framework do komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="67a89-143">Describes the various communications methods available in the .NET Framework for remote communications.</span></span>  
  
 [<span data-ttu-id="67a89-144">Utworzone za pomocą programu ASP.NET i klientami usługi XML sieci Web usług XML sieci Web</span><span class="sxs-lookup"><span data-stu-id="67a89-144">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 <span data-ttu-id="67a89-145">Zawiera tematy, które opisują oraz wyjaśniono, jak do usług XML sieci Web utworzony za pomocą programu ASP.NET programu.</span><span class="sxs-lookup"><span data-stu-id="67a89-145">Provides topics that describe and explain how to program XML Web services created using ASP.NET.</span></span>
