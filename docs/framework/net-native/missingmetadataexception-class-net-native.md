---
title: Klasa MissingMetadataException (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 607204081c71a4489a1a67ced24af12b150632e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="missingmetadataexception-class-net-native"></a>Klasa MissingMetadataException (architektura .NET Native)
**.NET dla aplikacji systemu Windows dla systemu Windows 10, [!INCLUDE[net_native](../../../includes/net-native-md.md)] tylko**  
  
 Wyjątek zgłaszany, gdy odbicia służy do pobierania metadanych, który nie jest obecny.  
  
 **Namespace:** System.Reflection  
  
> [!IMPORTANT]
>  `MissingMetadataException` Klasy jest przeznaczona wyłącznie do użytku wewnętrznego w [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia łańcucha. Nie jest przeznaczony do użycia w kodzie innych firm ani nie powinna obsługiwać wyjątek w kodzie aplikacji. Zamiast tego wyeliminować wyjątku przez dodanie wpisów z [pliku dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
## <a name="syntax"></a>Składnia  
 [!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]  
  
 Należy pamiętać, że `MissingMetadataException` pochodną klasy <xref:System.TypeAccessException>.  
  
 `MissingMetadataException` Klasa ma następujące elementy:  
  
## <a name="constructors"></a>Konstruktorów  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`public MissingMetadataException()`|Inicjuje nowe wystąpienie klasy `MissingMetadataException` przy użyciu systemu dostarczanego przez komunikatu opisującego błąd.<br /><br /> Ten konstruktor jest do użytku wewnętrznego przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia tylko łańcucha.|  
|`public MissingMetadataException(String message)`|Inicjuje nowe wystąpienie klasy `MissingMetadataException` klasy z powodu określonego błędu.<br /><br /> Ten konstruktor jest do użytku wewnętrznego przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] tylko torol łańcucha.|  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Pobiera kolekcję par klucz/wartość, które znajdują się dodatkowe zdefiniowane przez użytkownika informacje o wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Pobiera lub ustawia łącze do pliku Pomocy skojarzonych z tym wyjątkiem. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Pobiera lub ustawia `HRESULT`, kodowanych wartość liczbową będącą jest przypisany do określonego wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Pobiera bieżący wyjątek spowodował wyjątek. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Pobiera komunikat opisujący bieżący wyjątek. (Dziedziczone z <xref:System.TypeLoadException>.)|  
|`public string Source { get; set; }`|Pobiera lub ustawia nazwę aplikacji lub obiektu, który spowodował błąd. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Pobiera reprezentację ciągu natychmiastowego ramek na stosie wywołań. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Pobiera metodę, która zgłosiła bieżący wyjątek. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string TypeName { get; ]`|Pobiera pełną nazwę typu brakuje którego metadanych. (Dziedziczone z <xref:System.TypeLoadException>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Określa, czy określony obiekt jest równy bieżącemu obiektowi.  (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected void Finalize()`|Umożliwia obiektu, próby zwolnienia zasobów i wykonywać inne operacje oczyszczania, przed jego jest odzyskana przez wyrzucanie elementów bezużytecznych. (Dziedziczone z <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Zwraca wyjątek, który jest główną przyczynę jeden lub więcej kolejnych wyjątków. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Zwraca wartość skrótu dla `MissingMetadataException` wystąpienia.   (Dziedziczone z <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Ustawia <xref:System.Runtime.Serialization.SerializationInfo> obiektu o informacje o wyjątku.  (Dziedziczone z <xref:System.TypeLoadException>.)|  
|`public Type GetType()`|Pobiera typ środowiska uruchomieniowego bieżącego wystąpienia. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Tworzy kopię pobieżną bieżącego obiektu. (Dziedziczone z <xref:System.Object>.)|  
|`public string ToString()`|Zwraca reprezentację ciągu bieżącego wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Zdarzenia  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Występuje, gdy wyjątek jest serializowany można utworzyć obiektu stanu wyjątek, który zawiera seryjnych danych o wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Szczegóły użycia  
 `MissingMetadataException` Wyjątek podczas odbicia umożliwia dostęp do metadanych, które nie są dostępne w zestawie.  
  
 Metadane, który jest dostępny dla aplikacji w czasie wykonywania jest definiowana za pomocą pliku dyrektyw (Konfiguracja XML) środowiska uruchomieniowego, *. rd.xml. Aby zapobiec zgłaszanie tego wyjątku w aplikacji, należy zmodyfikować \*. rd.xml do definiowania metadanych, które musi znajdować się w czasie wykonywania. Informacje o formacie \*. pliku rd.xml, zobacz [dyrektyw środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Ponieważ ten wyjątek wskazuje, że metadane wymagane przez aplikację nie jest dostępny w czasie wykonywania, nie powinien obsługiwać tego wyjątku w `try` / `catch` bloku. Należy zdiagnozować przyczyną wyjątku i wyeliminować go przy użyciu pliku dyrektyw środowiska uruchomieniowego. Aby uzyskać wpisu, który można dodać do pliku dyrektyw środowiska uruchomieniowego, która eliminuje wyjątek, można użyć jednej z dwóch narzędzi do rozwiązywania problemów:  
>   
>  -   [MissingMetadataException Rozwiązywanie problemów z](http://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
> -   [MissingMetadataException Rozwiązywanie problemów z](http://dotnet.github.io/native/troubleshooter/method.html) dla metod.  
  
 `MissingMetadataException` Klasa nie zawiera unikatowych elementów członkowskich; wszystkich jego elementów członkowskich są dziedziczone z jej klasa podstawowa <xref:System.TypeAccessException>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Exception?displayProperty=nameWithType>  
 <xref:System.TypeAccessException>  
 [Klasa MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)  
 [Klasa MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)  
 [Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska wykonawczego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
