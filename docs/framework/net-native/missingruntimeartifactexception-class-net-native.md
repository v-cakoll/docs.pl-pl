---
title: Klasa MissingRuntimeArtifactException (architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
ms.openlocfilehash: 7a69add45202b3ad838de592fadc82a84fa0ba5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180969"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>Klasa MissingRuntimeArtifactException (architektura .NET Native)
**Aplikacje platformy .NET dla systemu Windows dla systemu Windows 10, tylko natywny dla platformy .NET**  
  
 Wyjątek, który jest zgłaszany, gdy metadane dla typu lub elementu członkowskiego typu jest dostępny, ale jego implementacja została usunięta.  
  
 **Obszar nazw:** System.reflection  
  
> [!IMPORTANT]
> Klasa `MissingRuntimeArtifactException` jest przeznaczona wyłącznie do użytku wewnętrznego przez łańcuch narzędzi .NET Native. Nie jest przeznaczony do użytku w kodzie innej firmy, ani nie należy obsługiwać wyjątek w kodzie aplikacji. Zamiast tego można wyeliminować wyjątek, dodając wpisy do [pliku dyrektyw środowiska wykonawczego](runtime-directives-rd-xml-configuration-file-reference.md). Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
## <a name="syntax"></a>Składnia  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 Należy zauważyć, że `MissingRuntimeArtifactException` <xref:System.MemberAccessException>klasa pochodzi od .  
  
 Klasa `MissingRuntimeArtifactException` ma następujące elementy członkowskie:  
  
## <a name="constructors"></a>Konstruktorów  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Inicjuje nowe wystąpienie `MissingRuntimeArtifactException` klasy przy użyciu komunikatu dostarczonego przez system, który opisuje błąd.<br /><br /> Ten konstruktor jest przeznaczony do użytku wewnętrznego tylko przez łańcuch narzędzi natywnych .NET.|  
|`public MissingRuntimeArtifactException(String message)`|Inicjuje nowe wystąpienie `MissingRuntimeArtifactException` klasy z określonym komunikatem o błędzie.<br /><br /> Ten konstruktor jest przeznaczony do użytku wewnętrznego tylko przez łańcuch narzędzi natywnych .NET.|  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Pobiera kolekcję par klucz/wartość, które zapewniają dodatkowe informacje zdefiniowane przez użytkownika o wyjątku. (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
|`public string HelpLink { get; set; }`|Pobiera lub ustawia łącze do pliku pomocy skojarzonego z tym wyjątkiem. (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
|`public int HResult { get; protected set; }`|Pobiera lub `HRESULT`ustawia , zakodowane wartości liczbowej, który jest przypisany do określonego wyjątku. (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
|`public Exception InnerException { get; }`|Pobiera wyjątek, który spowodował bieżący wyjątek. (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
|`public string Message { get; }`|Pobiera komunikat, który opisuje bieżący wyjątek. (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
|`public string Source { get; set; }`|Pobiera lub ustawia nazwę aplikacji lub obiektu, który spowodował błąd. (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
|`public string StackTrace { get; }`|Pobiera reprezentację ciągów ramek natychmiastowych na stosie wywołań. (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
|`public MethodBase TargetSite { get; }`|Pobiera metodę, która zgłosiła bieżący wyjątek. (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Określa, czy dany obiekt jest taki sam, jak bieżący obiekt.  (Odziedziczone <xref:System.Object>po .)|  
|`protected void Finalize()`|Umożliwia obiektowi, aby spróbować zwolnić zasoby i wykonać inne operacje oczyszczania, zanim zostanie odzyskany przez wyrzucanie elementów bezużytecznych. (Odziedziczone <xref:System.Object>po .)|  
|`public Exception GetBaseException()`|Zwraca wyjątek, który jest główną przyczyną jednego lub więcej kolejnych wyjątków. (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
|`public int GetHashCode()`|Zwraca kod skrótu `MissingRuntimeArtifactException` dla wystąpienia.   (Odziedziczone <xref:System.Object>po .)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Ustawia <xref:System.Runtime.Serialization.SerializationInfo> obiekt z informacjami o wyjątku.  (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
|`public Type GetType()`|Pobiera typ środowiska wykonawczego bieżącego wystąpienia. (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
|`protected Object MemberwiseClone()`|Tworzy płytką kopię bieżącego obiektu. (Odziedziczone <xref:System.Object>po .)|  
|`public string ToString()`|Zwraca reprezentację ciągu bieżącego wyjątku. (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
  
## <a name="events"></a>Zdarzenia  
  
|Wydarzenie|Opis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Występuje, gdy wyjątek jest serializowany, aby utworzyć obiekt stanu wyjątku, który zawiera szeregowane dane o wyjątku. (Odziedziczone <xref:System.Exception?displayProperty=nameWithType>po .)|  
  
## <a name="usage-details"></a>Szczegóły użycia  
 Wyjątek `MissingRuntimeArtifactException` jest zgłaszany, gdy podejmowana jest próba wystąpienia typu lub wywołania elementu członkowskiego typu i, mimo że metadane typu lub elementu członkowskiego są obecne, jego implementacja została usunięta.  
  
 Czy metadane i kod implementacji do dynamicznego wykonywania metody są dostępne dla aplikacji w czasie wykonywania \*jest zdefiniowany przez plik dyrektywy środowiska wykonawczego (konfiguracja XML), .rd.xml. Aby zapobiec zgłaszaniu tego wyjątku przez \*aplikację, należy zmodyfikować plik .rd.xml, aby upewnić się, że metadane wymagane przez typ lub typ elementu członkowskiego są obecne w czasie wykonywania. Aby uzyskać informacje o \*formacie pliku rd.xml, zobacz [Odwołanie do pliku konfiguracyjnego dyrektywy wykonawczej (rd.xml).](runtime-directives-rd-xml-configuration-file-reference.md)  
  
> [!IMPORTANT]
> Ponieważ ten wyjątek wskazuje, że kod implementacji wymagany przez aplikację nie jest dostępny w `try` / `catch` czasie wykonywania, nie należy obsługiwać tego wyjątku w bloku. Zamiast tego należy zdiagnozować przyczynę wyjątku i wyeliminować go przy użyciu pliku dyrektyw środowiska wykonawczego. Zazwyczaj można wyeliminować ten wyjątek, `Activate` określając `Dynamic` odpowiednie lub zasady dla elementu programu\*w pliku dyrektyw środowiska wykonawczego ( .rd.xml pliku). Aby uzyskać wpis, który można dodać do pliku dyrektyw środowiska uruchomieniowego, który eliminuje wyjątek, można użyć jednego z dwóch narzędzi do rozwiązywania problemów:  
>
> - [Narzędzie do rozwiązywania problemów z missingmetadataexception](https://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
> - [Narzędzie do rozwiązywania problemów z missingmetadataexception](https://dotnet.github.io/native/troubleshooter/method.html) dla metod.  
  
 Klasa `MissingRuntimeArtifactException` nie zawiera unikatowych elementów członkowskich; wszystkie jego elementy członkowskie są dziedziczone <xref:System.MemberAccessException>z jego klasy podstawowej, .  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
