---
title: Klasa MissingRuntimeArtifactException (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ba528f8545f0781f15e4479cbef0b80feeab46d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116847"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>Klasa MissingRuntimeArtifactException (architektura .NET Native)
**Platforma .NET dla aplikacji Windows dla systemu Windows 10, [!INCLUDE[net_native](../../../includes/net-native-md.md)] tylko**  
  
 Wyjątek, który jest zgłaszany, gdy metadane dla typu lub składowej typu jest dostępna, ale jego implementacja została usunięta.  
  
 **Namespace:** System.Reflection  
  
> [!IMPORTANT]
>  `MissingRuntimeArtifactException` Klasa jest przeznaczona wyłącznie do użytku wewnętrznego w [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi. Nie jest przeznaczony do użycia w kodzie innych firm, nie powinien obsługiwać wyjątek w kodzie aplikacji. Zamiast tego wyjątku można wyeliminować, dodając wpisów, aby Twoje [plik dyrektywy środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
## <a name="syntax"></a>Składnia  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 Należy pamiętać, że `MissingRuntimeArtifactException` klasa pochodzi od <xref:System.MemberAccessException>.  
  
 `MissingRuntimeArtifactException` Klasy ma następujące składowe:  
  
## <a name="constructors"></a>Konstruktorów  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Inicjuje nowe wystąpienie klasy `MissingRuntimeArtifactException` klasy za pomocą wiadomości dostarczone przez system, który opisuje błąd.<br /><br /> Ten konstruktor jest do użytku wewnętrznego przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] tylko łańcucha narzędzi.|  
|`public MissingRuntimeArtifactException(String message)`|Inicjuje nowe wystąpienie klasy `MissingRuntimeArtifactException` klasy przy użyciu określonego komunikatu o błędzie.<br /><br /> Ten konstruktor jest do użytku wewnętrznego przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] tylko łańcucha narzędzi.|  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Pobiera kolekcję par klucz/wartość, które zawierają dodatkowe informacje zdefiniowane przez użytkownika o wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Pobiera lub ustawia łącze, aby plik pomocy skojarzony z tym wyjątkiem. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Pobiera lub ustawia `HRESULT`, kodowane wartość liczbowa, która jest przypisana do określonego wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Pobiera wyjątek, który spowodował bieżący wyjątek. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Pobiera komunikat, który opisuje bieżący wyjątek. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Source { get; set; }`|Pobiera lub ustawia nazwę aplikacji lub obiektu, który spowodował błąd. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Pobiera reprezentację ciągu natychmiastowego ramek na stosie wywołań. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Pobiera metodę, która zgłosiła wyjątek bieżący. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Określa, czy określony obiekt jest równy bieżącemu obiektowi.  (Dziedziczone z <xref:System.Object>.)|  
|`protected void Finalize()`|Umożliwia obiektu spróbuj zwolnić zasoby i wykonywać inne operacje oczyszczania, zanim go jest odzyskiwane przez wyrzucanie elementów bezużytecznych. (Dziedziczone z <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Zwraca wyjątek, który jest główną przyczynę jeden lub kilka kolejnych wyjątków. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Zwraca wartość skrótu dla `MissingRuntimeArtifactException` wystąpienia.   (Dziedziczone z <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Zestawy <xref:System.Runtime.Serialization.SerializationInfo> obiektów z informacją o wyjątku.  (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Pobiera typ środowiska uruchomieniowego bieżącego wystąpienia. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Tworzy płytką kopię bieżącego obiektu. (Dziedziczone z <xref:System.Object>.)|  
|`public string ToString()`|Zwraca reprezentację ciągu bieżącego wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Zdarzenia  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Występuje, gdy wyjątek jest serializowana. Aby utworzyć obiekt stan wyjątku, który zawiera serializowane dane o wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Szczegóły użycia  
 `MissingRuntimeArtifactException` Wyjątek jest zgłaszany, gdy jest podejmowana próba tworzenia wystąpienia typu lub składowej typu wywołania i, mimo że typu lub elementu członkowskiego metadanych jest obecny, jego implementacja została usunięta.  
  
 Czy metadanych i kod implementacji, aby dynamicznie wykonania metody są dostępne dla aplikacji w czasie wykonywania jest definiowany przez plik dyrektywy (Konfiguracja XML) środowiska uruchomieniowego, \*. rd.xml. Aby zapobiec sytuacji, w której aplikacja zostanie zgłoszony wyjątek, należy zmodyfikować \*. rd.xml, aby upewnić się, że metadane wymagane przez dany typ lub członek typu znajduje się w czasie wykonywania. Aby uzyskać informacje o formacie parametru \*. plik rd.xml zobacz [dyrektywy środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Ponieważ ten wyjątek wskazuje, że kod implementacji, wymagane przez aplikację nie jest dostępna w czasie wykonywania, nie powinien obsługiwać tego wyjątku w `try` / `catch` bloku. Zamiast tego należy przyczynę wyjątku i wyeliminuj je przy użyciu pliku dyrektyw środowiska uruchomieniowego. Zazwyczaj można wyeliminować ten wyjątek, określając odpowiednią `Activate` lub `Dynamic` zasad dla elementu programu w pliku dyrektyw środowiska uruchomieniowego (\*. plik rd.xml). Aby uzyskać wpis, który można dodać do pliku dyrektyw środowiska uruchomieniowego, które eliminuje wyjątku, można użyć jednej z dwóch narzędzi do rozwiązywania problemów:  
>   
> - [MissingMetadataException narzędzia do rozwiązywania problemów](https://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
> - [MissingMetadataException narzędzia do rozwiązywania problemów](https://dotnet.github.io/native/troubleshooter/method.html) dla metod.  
  
 `MissingRuntimeArtifactException` Klasy nie zawiera unikatowych elementów członkowskich; wszystkie jego elementy członkowskie są dziedziczone od swojej klasy bazowej <xref:System.MemberAccessException>.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
