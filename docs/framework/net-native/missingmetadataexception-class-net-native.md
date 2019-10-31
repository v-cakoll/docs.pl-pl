---
title: Klasa MissingMetadataException (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
ms.openlocfilehash: d73d66529bc30358c946eb0a7072f0cb8910b19a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128288"
---
# <a name="missingmetadataexception-class-net-native"></a>Klasa MissingMetadataException (architektura .NET Native)

**Aplikacje .NET dla systemu Windows 10, tylko .NET Native**

Wyjątek, który jest generowany, gdy odbicie jest używane do pobierania nieobecnych metadanych.

**Przestrzeń nazw:** System. odbicie

> [!IMPORTANT]
> Klasa `MissingMetadataException` jest przeznaczona wyłącznie do użytku wewnętrznego w łańcuchu narzędzi .NET Native. Nie jest on przeznaczony do użycia w kodzie innej firmy ani nie powinien obsługiwać wyjątku w kodzie aplikacji. Zamiast tego należy wyeliminować wyjątek poprzez dodanie wpisów do [pliku dyrektywy środowiska uruchomieniowego](runtime-directives-rd-xml-configuration-file-reference.md). Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.

## <a name="syntax"></a>Składnia

[!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]

Należy zauważyć, że Klasa `MissingMetadataException` dziedziczy z <xref:System.TypeAccessException>.

Klasa `MissingMetadataException` ma następujących członków:

## <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-----------------|-----------------|
|`public MissingMetadataException()`|Inicjuje nowe wystąpienie klasy `MissingMetadataException` przy użyciu komunikatu dostarczonego przez system, który opisuje błąd.<br /><br /> Ten konstruktor jest przeznaczony do użytku wewnętrznego tylko przez łańcuch narzędzi .NET Native.|
|`public MissingMetadataException(String message)`|Inicjuje nowe wystąpienie klasy `MissingMetadataException` z określonym komunikatem o błędzie.<br /><br /> Ten konstruktor jest przeznaczony do użytku wewnętrznego tylko przez łańcuch narzędzi .NET Native.|

## <a name="properties"></a>Właściwości

|Właściwość|Opis|
|--------------|-----------------|
|`public IDictionary Data { get; }`|Pobiera kolekcję par klucz/wartość, które zawierają dodatkowe informacje zdefiniowane przez użytkownika dotyczące wyjątku. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string HelpLink { get; set; }`|Pobiera lub ustawia link do pliku pomocy skojarzonego z tym wyjątkiem. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public int HResult { get; protected set; }`|Pobiera lub ustawia `HRESULT`, kodowanej wartości liczbowej przypisanej do określonego wyjątku. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public Exception InnerException { get; }`|Pobiera wyjątek, który spowodował bieżący wyjątek. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string Message { get; }`|Pobiera komunikat, który opisuje bieżący wyjątek. (Odziedziczone z <xref:System.TypeLoadException>.)|
|`public string Source { get; set; }`|Pobiera lub ustawia nazwę aplikacji lub obiektu, który spowodował błąd. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string StackTrace { get; }`|Pobiera ciąg reprezentujący bezpośrednie ramki w stosie wywołań. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public MethodBase TargetSite { get; }`|Pobiera metodę, która wywołała bieżący wyjątek. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string TypeName { get; ]`|Pobiera w pełni kwalifikowaną nazwę typu, którego nie ma w metadanych. (Odziedziczone z <xref:System.TypeLoadException>.)|

## <a name="methods"></a>Metody

|Metoda|Opis|
|------------|-----------------|
|`public bool Equals(Object obj)`|Określa, czy określony obiekt jest równy bieżącemu obiektowi.  (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|
|`protected void Finalize()`|Umożliwia obiektowi podjęcie próby zwolnienia zasobów i wykonywanie innych operacji czyszczenia przed odinstalowaniem ich przez wyrzucanie elementów bezużytecznych. (Odziedziczone z <xref:System.Object>.)|
|`public Exception GetBaseException()`|Zwraca wyjątek, który jest główną przyczyną jednego lub kilku kolejnych wyjątków. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|
|`public int GetHashCode()`|Zwraca kod skrótu wystąpienia `MissingMetadataException`.   (Odziedziczone z <xref:System.Object>.)|
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Ustawia obiekt <xref:System.Runtime.Serialization.SerializationInfo> zawierający informacje o wyjątku.  (Odziedziczone z <xref:System.TypeLoadException>.)|
|`public Type GetType()`|Pobiera typ środowiska uruchomieniowego bieżącego wystąpienia. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|
|`protected Object MemberwiseClone()`|Tworzy skróconą kopię bieżącego obiektu. (Odziedziczone z <xref:System.Object>.)|
|`public string ToString()`|Zwraca ciąg reprezentujący bieżący wyjątek. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|

## <a name="events"></a>Zdarzenia

|Zdarzenie|Opis|
|-----------|-----------------|
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Występuje, gdy wyjątek jest serializowany w celu utworzenia obiektu stanu wyjątku, który zawiera serializowane dane dotyczące wyjątku. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|

## <a name="usage-details"></a>Szczegóły użycia

Wyjątek `MissingMetadataException` jest generowany, gdy odbicie jest używane w celu uzyskania dostępu do metadanych, które nie są dostępne w zestawie.

Metadane dostępne dla aplikacji w czasie wykonywania są zdefiniowane w plikach dyrektywy środowiska uruchomieniowego (konfiguracja XML), \*. Rd. XML. Aby zapobiec zgłaszaniu tego wyjątku przez aplikację, należy zmodyfikować \*. Rd. XML w celu zdefiniowania metadanych, które muszą być obecne w czasie wykonywania. Aby uzyskać informacje o formacie pliku \*. Rd. XML, zobacz [Dokumentacja pliku konfiguracji dyrektywy środowiska uruchomieniowego (RD. xml)](runtime-directives-rd-xml-configuration-file-reference.md).

> [!IMPORTANT]
> Ponieważ ten wyjątek wskazuje, że metadane potrzebne przez aplikację nie są dostępne w czasie wykonywania, nie należy obsługiwać tego wyjątku w bloku `try`/`catch`. Zamiast tego należy zdiagnozować przyczynę wyjątku i wyeliminować go przy użyciu pliku dyrektywy środowiska uruchomieniowego. Aby uzyskać wpis, który można dodać do pliku dyrektywy środowiska uruchomieniowego, który eliminuje wyjątek, można użyć jednego z dwóch narzędzi do rozwiązywania problemów:
>
> - [Narzędzie do rozwiązywania problemów z MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) dla typów.
> - [Narzędzie do rozwiązywania problemów z MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) .

Klasa `MissingMetadataException` nie zawiera żadnych unikatowych elementów członkowskich; wszystkie jego elementy członkowskie są dziedziczone z klasy podstawowej, <xref:System.TypeAccessException>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.TypeAccessException>
- [Klasa MissingInteropDataException](missinginteropdataexception-class-net-native.md)
- [Klasa MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
