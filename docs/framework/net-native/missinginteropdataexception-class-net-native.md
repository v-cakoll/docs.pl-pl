---
title: Klasa MissingInteropDataException (architektura .NET Native)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d916aa5e19b8ce583984d9a8e9708d34cf0adfb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049544"
---
# <a name="missinginteropdataexception-class-net-native"></a>Klasa MissingInteropDataException (architektura .NET Native)
**Aplikacje .NET dla systemu Windows 10, tylko .NET Native**  
  
 Wyjątek, który jest generowany, gdy wywoływana jest metoda ręcznego kierowania, ale nie można odnaleźć metadanych dla typu przez analizę statyczną lub plik dyrektywy środowiska uruchomieniowego.  
  
 **Obszaru** System.Runtime.CompilerServices  
  
> [!IMPORTANT]
> `MissingInteropDataException` Klasa jest przeznaczona wyłącznie do użytku wewnętrznego w łańcuchu narzędzi .NET Native. Nie jest on przeznaczony do użycia w kodzie innej firmy ani nie powinien obsługiwać wyjątku w kodzie aplikacji. Zamiast tego należy wyeliminować wyjątek poprzez dodanie wpisów do [pliku dyrektywy środowiska uruchomieniowego](runtime-directives-rd-xml-configuration-file-reference.md). Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
## <a name="syntax"></a>Składnia  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 `MissingInteropDataException` Klasa ma następujących członków:  
  
## <a name="constructors"></a>Konstruktorów  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|Inicjuje nowe wystąpienie `MissingInteropDataException` klasy przy użyciu identyfikatora komunikatu dostarczonego przez system, który opisuje błąd i typ, którego dane są niedostępne. Ten konstruktor jest przeznaczony do użytku wewnętrznego tylko przez łańcuch narzędzi .NET Native.|  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Pobiera kolekcję par klucz/wartość, które zawierają dodatkowe informacje zdefiniowane przez użytkownika dotyczące wyjątku. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Pobiera lub ustawia link do pliku pomocy skojarzonego z tym wyjątkiem. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Pobiera lub ustawia `HRESULT`wartość, która jest zakodowaną wartością liczbową, która jest przypisana do określonego wyjątku. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Pobiera wyjątek, który spowodował bieżący wyjątek. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Pobiera komunikat, który opisuje bieżący wyjątek. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type MissingType { get; private set; }`|Pobiera lub ustawia typ, którego brakuje danych.|  
|`public string Source { get; set; }`|Pobiera lub ustawia nazwę aplikacji lub obiektu, który spowodował błąd. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Pobiera ciąg reprezentujący bezpośrednie ramki w stosie wywołań. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Pobiera metodę, która wywołała bieżący wyjątek. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Określa, czy określony obiekt jest równy bieżącemu obiektowi.  (Odziedziczone z <xref:System.Object>.)|  
|`protected void Finalize()`|Umożliwia obiektowi podjęcie próby zwolnienia zasobów i wykonywanie innych operacji czyszczenia przed odinstalowaniem ich przez wyrzucanie elementów bezużytecznych. (Odziedziczone z <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Zwraca wyjątek, który jest główną przyczyną jednego lub kilku kolejnych wyjątków. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Zwraca kod skrótu dla `MissingInteropDataException` wystąpienia.   (Odziedziczone z <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|<xref:System.Runtime.Serialization.SerializationInfo> Ustawia obiekt z informacjami o wyjątku.  (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Pobiera typ środowiska uruchomieniowego bieżącego wystąpienia. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Tworzy skróconą kopię bieżącego obiektu. (Odziedziczone z <xref:System.Object>.)|  
|`public string ToString()`|Zwraca ciąg reprezentujący bieżący wyjątek. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Zdarzenia  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Występuje, gdy wyjątek jest serializowany w celu utworzenia obiektu stanu wyjątku, który zawiera serializowane dane dotyczące wyjątku. (Odziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Szczegóły użycia  
 Wyjątek `MissingInteropDataException` jest zgłaszany, gdy wywołanie metody do składnika com lub środowisko wykonawcze systemu Windows nie może zostać wykonane pomyślnie, ponieważ informacje o typie są niedostępne.  
  
 Metadane dostępne dla aplikacji w czasie wykonywania są zdefiniowane przez dyrektywy środowiska uruchomieniowego (XML Configuration), \*. Rd. XML. Aby zapobiec zgłaszaniu tego wyjątku przez aplikację, należy zmodyfikować ten plik w celu zdefiniowania metadanych, które muszą być obecne w czasie wykonywania. Najczęściej można rozwiązać ten problem, dodając `MarshalObject`atrybut, `MarshalDelegate`lub `MarshalStructure` do odpowiedniego elementu programu w pliku dyrektywy środowiska uruchomieniowego. Aby uzyskać informacje o formacie tego pliku, zobacz [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (RD. xml)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Ponieważ ten wyjątek wskazuje, że metadane potrzebne przez aplikację nie są dostępne w czasie wykonywania, nie należy obsługiwać tego wyjątku w `try` / `catch` bloku. Zamiast tego należy zdiagnozować przyczynę wyjątku i wyeliminować go przez dodanie odpowiedniego wpisu do pliku dyrektywy środowiska uruchomieniowego.  
  
 Klasa zawiera pojedynczy unikatowy element członkowski `MissingType` , właściwość, która wskazuje typ, którego metadane są zbędne dla pomyślnego wywołania metody. `MissingInteropDataException` Wszystkie pozostałe elementy członkowskie są dziedziczone z klasy podstawowej, <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Exception?displayProperty=nameWithType>
- [Klasa MissingMetadataException](missingmetadataexception-class-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
