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
# <a name="binary-serialization"></a>Serializacja binarna

Serializacja mogą być definiowane jako proces przechowywania stanu obiektu na nośniku. W trakcie tego procesu publiczny i prywatny pola obiektu oraz nazwę klasy, łącznie z zestawu zawierającego klasy, są konwertowane na strumień bajtów, które są następnie zapisywane do strumienia danych. Gdy obiekt jest następnie przeprowadzona, dokładną oryginalnego obiektu zostanie utworzony.

Podczas implementowania mechanizmu serializacji w środowisku zorientowane obiektowo, konieczne będzie wprowadzenie numeru kompromisów między łatwość użycia i elastyczność. Ten proces można automatycznego w dużym stopniu, pod warunkiem, że podane są wystarczające kontrolę nad procesem. Na przykład sytuacji mogą wystąpić podczas gdzie proste serializacji binarnej jest niewystarczająca lub może być powód, aby określić pola, które w klasie muszą być serializowane. W poniższych sekcjach zbadać mechanizmu serializacji niezawodne dostarczony wraz z programem .NET i zaznacz wiele ważnych funkcji, które umożliwiają dostosowanie procesu do własnych potrzeb.

> [!NOTE]
> Stan UTF-8 lub UTF-7 kodowany obiektu nie jest zachowana, jeśli obiekt jest serializacji i deserializacji za pomocą różnych wersji programu .NET Framework.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Jak rodzaj serializacji binarnej pozwala na modyfikację prywatne elementy członkowskie wewnątrz i dlatego zmiany stanu tego obiektu, zaleca się innych platform serializacji jak JSON.NET, które działają w publicznej powierzchni interfejsu API.

## <a name="binary-serialization-in-net-core"></a>Serializacja binarna w .NET Core

Oprogramowanie .NET core obsługuje serializacji binarnej z podzbioru typów. Można wyświetlić listę obsługiwanych typów w [sekcji typów możliwych do serializacji](#serializable-types). Zestaw określonych typów zapewniona jest możliwy do serializacji między .NET Framework 4.5.1 i nowszych wersjach i .NET Core 2.0 i nowszych wersjach. Inne implementacje .NET, takie jak Mono, oficjalnie nie są obsługiwane, ale również powinny działać.

### <a name="serializable-types"></a>Typów możliwych do serializacji

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
- <xref:System.DBNull?displayProperty=nameWithType>(dostępne w .NET Core pkt 2.0.2 i nowsze wersje)   
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
- <xref:System.ValueTuple?displayProperty=nameWithType>(nie można serializować w .NET Framework 4.7 i wcześniejsze wersje)  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   

## <a name="in-this-section"></a>W tej sekcji

 [Pojęcia dotyczące serializacji](../../../docs/standard/serialization/serialization-concepts.md)  
 Opisano dwa scenariusze, w których serializacji jest użyteczny: gdy trwałych danych do magazynu i przekazywanie obiektów między domenami aplikacji.  
  
 [Podstawowe serializacji](../../../docs/standard/serialization/basic-serialization.md)  
 Opisuje sposób używania PLiku binarnego i SOAP elementy formatujące do wykonywania serializacji obiektów.  
  
 [Selektywne serializacji](../../../docs/standard/serialization/selective-serialization.md)  
 Opisuje sposób zapobiegania serializacji niektórych składowych klasy.  
  
 [Niestandardowej serializacji](../../../docs/standard/serialization/custom-serialization.md)  
 Opisuje sposób dostosowywania serializacji dla klasy przy użyciu <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
 [Kroki procesu serializacji](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 Opisuje kurs akcji serializacji przyjmuje, gdy <xref:System.Runtime.Serialization.Formatter.Serialize%2A> metoda jest wywoływana w elementu formatującego.  
  
 [Serializacji z tolerancją dla wersji](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 Wyjaśnia sposób tworzenia typów możliwych do serializacji, które mogą być modyfikowane w czasie bez powodowania aplikacjom zgłaszają wyjątki.  
  
 [Wytyczne serializacji](../../../docs/standard/serialization/serialization-guidelines.md)  
 Zawiera ogólne zasady ustalania, kiedy można serializować obiektu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Runtime.Serialization>  
 Zawiera klasy, które mogą być używane do serializacji i deserializacji obiektów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [XML i serializacji SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Opisuje mechanizm serializacji XML, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.  
  
 [Zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md)  
 Opisuje bezpiecznego wskazówek kodowania, które należy wykonać podczas pisania kodu, który będzie wykonywać serializacji.  
  
 [Obiekty zdalnego](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 Opis różnych metod komunikacji dostępnych w programie .NET Framework do komunikacji zdalnej.  
  
 [Utworzone za pomocą programu ASP.NET i klientami usługi XML sieci Web usług XML sieci Web](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 Zawiera tematy, które opisują oraz wyjaśniono, jak do usług XML sieci Web utworzony za pomocą programu ASP.NET programu.
