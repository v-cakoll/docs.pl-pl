---
title: Klasa MissingRuntimeArtifactException (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7b138aec8a64683ca4b42cbbc8bd3584c06cc90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="missingruntimeartifactexception-class-net-native"></a>Klasa MissingRuntimeArtifactException (architektura .NET Native)
**.NET dla aplikacji systemu Windows dla systemu Windows 10, [!INCLUDE[net_native](../../../includes/net-native-md.md)] tylko**  
  
 Wyjątek zgłaszany, gdy metadane dla typu lub elementu członkowskiego typu są dostępne, ale jej implementacja została usunięta.  
  
 **Namespace:** System.Reflection  
  
> [!IMPORTANT]
>  `MissingRuntimeArtifactException` Klasy jest przeznaczona wyłącznie do użytku wewnętrznego w [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia łańcucha. Nie jest przeznaczony do użycia w kodzie innych firm ani nie powinna obsługiwać wyjątek w kodzie aplikacji. Zamiast tego wyeliminować wyjątku przez dodanie wpisów z [pliku dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
## <a name="syntax"></a>Składnia  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 Należy pamiętać, że `MissingRuntimeArtifactException` pochodną klasy <xref:System.MemberAccessException>.  
  
 `MissingRuntimeArtifactException` Klasa ma następujące elementy:  
  
## <a name="constructors"></a>Konstruktorów  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Inicjuje nowe wystąpienie klasy `MissingRuntimeArtifactException` przy użyciu systemu dostarczanego przez komunikatu opisującego błąd.<br /><br /> Ten konstruktor jest do użytku wewnętrznego przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia tylko łańcucha.|  
|`public MissingRuntimeArtifactException(String message)`|Inicjuje nowe wystąpienie klasy `MissingRuntimeArtifactException` klasy z powodu określonego błędu.<br /><br /> Ten konstruktor jest do użytku wewnętrznego przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia tylko łańcucha.|  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Pobiera kolekcję par klucz/wartość, które znajdują się dodatkowe zdefiniowane przez użytkownika informacje o wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Pobiera lub ustawia łącze do pliku Pomocy skojarzonych z tym wyjątkiem. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Pobiera lub ustawia `HRESULT`, kodowanych wartość liczbową będącą jest przypisany do określonego wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Pobiera bieżący wyjątek spowodował wyjątek. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Pobiera komunikat opisujący bieżący wyjątek. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Source { get; set; }`|Pobiera lub ustawia nazwę aplikacji lub obiektu, który spowodował błąd. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Pobiera reprezentację ciągu natychmiastowego ramek na stosie wywołań. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Pobiera metodę, która zgłosiła bieżący wyjątek. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Określa, czy określony obiekt jest równy bieżącemu obiektowi.  (Dziedziczone z <xref:System.Object>.)|  
|`protected void Finalize()`|Umożliwia obiektu, próby zwolnienia zasobów i wykonywać inne operacje oczyszczania, przed jego jest odzyskana przez wyrzucanie elementów bezużytecznych. (Dziedziczone z <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Zwraca wyjątek, który jest główną przyczynę jeden lub więcej kolejnych wyjątków. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Zwraca wartość skrótu dla `MissingRuntimeArtifactException` wystąpienia.   (Dziedziczone z <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Ustawia <xref:System.Runtime.Serialization.SerializationInfo> obiektu o informacje o wyjątku.  (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Pobiera typ środowiska uruchomieniowego bieżącego wystąpienia. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Tworzy kopię pobieżną bieżącego obiektu. (Dziedziczone z <xref:System.Object>.)|  
|`public string ToString()`|Zwraca reprezentację ciągu bieżącego wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Zdarzenia  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Występuje, gdy wyjątek jest serializowany można utworzyć obiektu stanu wyjątek, który zawiera seryjnych danych o wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Szczegóły użycia  
 `MissingRuntimeArtifactException` Wyjątek podczas próby utworzenia wystąpienia typu lub wywołanie członka typu i, choć tego typu lub elementu członkowskiego metadanych jest obecny, jego implementacja została usunięta.  
  
 Określa, czy metadane i kod implementacji, aby dynamicznie wykonania metody są dostępne dla aplikacji w czasie wykonywania jest zdefiniowany w pliku dyrektyw (Konfiguracja XML) środowiska uruchomieniowego, *. rd.xml. Aby zapobiec zgłaszanie tego wyjątku w aplikacji, należy zmodyfikować \*. rd.xml, aby upewnić się, czy metadane wymagane według typu lub elementu członkowskiego typu znajduje się w czasie wykonywania. Informacje o formacie \*. pliku rd.xml, zobacz [dyrektyw środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Ponieważ ten wyjątek wskazuje, że kod implementacji wymaga aplikacja nie jest dostępna w czasie wykonywania, nie powinien obsługiwać tego wyjątku w `try` / `catch` bloku. Należy zdiagnozować przyczyną wyjątku i wyeliminować go przy użyciu pliku dyrektyw środowiska uruchomieniowego. Zazwyczaj wyeliminować ten wyjątek, określając odpowiedni `Activate` lub `Dynamic` zasad dla elementu programu w pliku dyrektyw środowiska uruchomieniowego (*. pliku rd.xml). Aby uzyskać wpisu, który można dodać do pliku dyrektyw środowiska uruchomieniowego, która eliminuje wyjątek, można użyć jednej z dwóch narzędzi do rozwiązywania problemów:  
>   
>  -   [MissingMetadataException Rozwiązywanie problemów z](http://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
> -   [MissingMetadataException Rozwiązywanie problemów z](http://dotnet.github.io/native/troubleshooter/method.html) dla metod.  
  
 `MissingRuntimeArtifactException` Klasa nie zawiera unikatowych elementów członkowskich; wszystkich jego elementów członkowskich są dziedziczone z jej klasa podstawowa <xref:System.MemberAccessException>.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
