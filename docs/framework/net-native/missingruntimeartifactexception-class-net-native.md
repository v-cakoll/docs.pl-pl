---
title: Klasa MissingRuntimeArtifactException (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
ms.openlocfilehash: 7a69add45202b3ad838de592fadc82a84fa0ba5d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180969"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>Klasa MissingRuntimeArtifactException (architektura .NET Native)
**Aplikacje .NET dla systemu Windows 10, tylko .NET Native**  
  
 Wyjątek, który jest generowany, gdy jest dostępny metadanych typu lub elementu członkowskiego typu, ale jego implementacja została usunięta.  
  
 **Przestrzeń nazw:** System. odbicie  
  
> [!IMPORTANT]
> `MissingRuntimeArtifactException`Klasa jest przeznaczona wyłącznie do użytku wewnętrznego w łańcuchu narzędzi .NET Native. Nie jest on przeznaczony do użycia w kodzie innej firmy ani nie powinien obsługiwać wyjątku w kodzie aplikacji. Zamiast tego należy wyeliminować wyjątek poprzez dodanie wpisów do [pliku dyrektywy środowiska uruchomieniowego](runtime-directives-rd-xml-configuration-file-reference.md). Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
## <a name="syntax"></a>Składnia  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 Należy zauważyć, że `MissingRuntimeArtifactException` Klasa pochodzi od <xref:System.MemberAccessException> .  
  
 `MissingRuntimeArtifactException`Klasa ma następujących członków:  
  
## <a name="constructors"></a>Konstruktory  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Inicjuje nowe wystąpienie `MissingRuntimeArtifactException` klasy przy użyciu komunikatu dostarczonego przez system, który opisuje błąd.<br /><br /> Ten konstruktor jest przeznaczony do użytku wewnętrznego tylko przez łańcuch narzędzi .NET Native.|  
|`public MissingRuntimeArtifactException(String message)`|Inicjuje nowe wystąpienie `MissingRuntimeArtifactException` klasy z określonym komunikatem o błędzie.<br /><br /> Ten konstruktor jest przeznaczony do użytku wewnętrznego tylko przez łańcuch narzędzi .NET Native.|  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Pobiera kolekcję par klucz/wartość, które zawierają dodatkowe informacje zdefiniowane przez użytkownika dotyczące wyjątku. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string HelpLink { get; set; }`|Pobiera lub ustawia link do pliku pomocy skojarzonego z tym wyjątkiem. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public int HResult { get; protected set; }`|Pobiera lub ustawia `HRESULT` zakodowaną wartość liczbową, która jest przypisana do określonego wyjątku. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public Exception InnerException { get; }`|Pobiera wyjątek, który spowodował bieżący wyjątek. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string Message { get; }`|Pobiera komunikat, który opisuje bieżący wyjątek. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string Source { get; set; }`|Pobiera lub ustawia nazwę aplikacji lub obiektu, który spowodował błąd. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string StackTrace { get; }`|Pobiera ciąg reprezentujący bezpośrednie ramki w stosie wywołań. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public MethodBase TargetSite { get; }`|Pobiera metodę, która wywołała bieżący wyjątek. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Określa, czy dany obiekt jest taki sam, jak bieżący obiekt.  (Odziedziczone z <xref:System.Object> .)|  
|`protected void Finalize()`|Umożliwia obiektowi podjęcie próby zwolnienia zasobów i wykonywanie innych operacji czyszczenia przed odinstalowaniem ich przez wyrzucanie elementów bezużytecznych. (Odziedziczone z <xref:System.Object> .)|  
|`public Exception GetBaseException()`|Zwraca wyjątek, który jest główną przyczyną jednego lub kilku kolejnych wyjątków. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public int GetHashCode()`|Zwraca kod skrótu dla `MissingRuntimeArtifactException` wystąpienia.   (Odziedziczone z <xref:System.Object> .)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Ustawia <xref:System.Runtime.Serialization.SerializationInfo> obiekt z informacjami o wyjątku.  (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public Type GetType()`|Pobiera typ środowiska uruchomieniowego bieżącego wystąpienia. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
|`protected Object MemberwiseClone()`|Tworzy skróconą kopię bieżącego obiektu. (Odziedziczone z <xref:System.Object> .)|  
|`public string ToString()`|Zwraca ciąg reprezentujący bieżący wyjątek. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
  
## <a name="events"></a>Zdarzenia  
  
|Wydarzenie|Opis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Występuje, gdy wyjątek jest serializowany w celu utworzenia obiektu stanu wyjątku, który zawiera serializowane dane dotyczące wyjątku. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType> .)|  
  
## <a name="usage-details"></a>Szczegóły użycia  
 `MissingRuntimeArtifactException`Wyjątek jest zgłaszany, gdy podejmowana jest próba utworzenia wystąpienia typu lub wywołania elementu członkowskiego typu, chociaż istnieją metadane typu lub elementu członkowskiego. jego implementacja została usunięta.  
  
 Czy metadane i kod implementacji do dynamicznego wykonywania metody są dostępne dla aplikacji w czasie wykonywania jest zdefiniowany przez dyrektywy środowiska uruchomieniowego (XML Configuration), \* . Rd. XML. Aby zapobiec zgłaszaniu tego wyjątku przez aplikację, należy zmodyfikować \* plik RD. XML, aby upewnić się, że metadane wymagane przez typ lub składową typu są obecne w czasie wykonywania. Aby uzyskać informacje o formacie \* pliku Rd. XML, zobacz [Dokumentacja pliku konfiguracji dyrektywy środowiska uruchomieniowego (RD. xml)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Ponieważ ten wyjątek wskazuje, że kod implementacji wymagany przez aplikację nie jest dostępny w czasie wykonywania, nie należy obsługiwać tego wyjątku w `try` / `catch` bloku. Zamiast tego należy zdiagnozować przyczynę wyjątku i wyeliminować go przy użyciu pliku dyrektywy środowiska uruchomieniowego. Zwykle eliminujesz ten wyjątek, określając odpowiednie `Activate` `Dynamic` zasady lub zasad dla elementu programu w pliku dyrektywy środowiska uruchomieniowego ( \* plik. Rd. xml). Aby uzyskać wpis, który można dodać do pliku dyrektywy środowiska uruchomieniowego, który eliminuje wyjątek, można użyć jednego z dwóch narzędzi do rozwiązywania problemów:  
>
> - [Narzędzie do rozwiązywania problemów z MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
> - [Narzędzie do rozwiązywania problemów z MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
 `MissingRuntimeArtifactException`Klasa nie zawiera żadnych unikatowych elementów członkowskich; wszystkie jej elementy członkowskie są dziedziczone z klasy podstawowej, <xref:System.MemberAccessException> .  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
