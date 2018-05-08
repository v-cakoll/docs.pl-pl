---
title: Klasa MissingInteropDataException (architektura .NET Native)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 189b50b4d35d061c511fbd06cc843296607062b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="missinginteropdataexception-class-net-native"></a>Klasa MissingInteropDataException (architektura .NET Native)
**.NET dla aplikacji systemu Windows dla systemu Windows 10, [!INCLUDE[net_native](../../../includes/net-native-md.md)] tylko**  
  
 Wyjątek zgłaszany, gdy ręcznego przekazywania międzyprocesowego — metoda jest wywoływana, ale metadanych dla typu nie zostanie odnaleziony przez analizę statyczną lub w pliku dyrektyw środowiska uruchomieniowego.  
  
 **Namespace:** System.Runtime.CompilerServices  
  
> [!IMPORTANT]
>  `MissingInteropDataException` Klasy jest przeznaczona wyłącznie do użytku wewnętrznego w [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia łańcucha. Nie jest przeznaczony do użycia w kodzie innych firm ani nie powinna obsługiwać wyjątek w kodzie aplikacji. Zamiast tego wyeliminować wyjątku przez dodanie wpisów z [pliku dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
## <a name="syntax"></a>Składnia  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 `MissingInteropDataException` Klasa ma następujące elementy:  
  
## <a name="constructors"></a>Konstruktorów  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|Inicjuje nowe wystąpienie klasy `MissingInteropDataException` przy użyciu Identyfikatora dostarczany przez system komunikat, który opisuje błąd i typu danych, których brakuje. Ten konstruktor jest do użytku wewnętrznego przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia tylko łańcucha.|  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Pobiera kolekcję par klucz/wartość, które znajdują się dodatkowe zdefiniowane przez użytkownika informacje o wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Pobiera lub ustawia łącze do pliku Pomocy skojarzonych z tym wyjątkiem. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Pobiera lub ustawia `HRESULT`, czyli wartość liczbową kodowane jest przypisany do określonego wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Pobiera bieżący wyjątek spowodował wyjątek. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Pobiera komunikat opisujący bieżący wyjątek. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type MissingType { get; private set; }`|Pobiera lub ustawia typ danych, których nie istnieje.|  
|`public string Source { get; set; }`|Pobiera lub ustawia nazwę aplikacji lub obiekt, który spowodował błąd. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Pobiera reprezentację ciągu natychmiastowego ramek na stosie wywołań. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Pobiera metodę, która zgłosiła bieżący wyjątek. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Określa, czy określony obiekt jest równy bieżącemu obiektowi.  (Dziedziczone z <xref:System.Object>.)|  
|`protected void Finalize()`|Umożliwia obiektu, próby zwolnienia zasobów i wykonywać inne operacje oczyszczania, przed jego jest odzyskana przez wyrzucanie elementów bezużytecznych. (Dziedziczone z <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Zwraca wyjątek, który jest główną przyczynę jeden lub więcej kolejnych wyjątków. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Zwraca wartość skrótu dla `MissingInteropDataException` wystąpienia.   (Dziedziczone z <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Ustawia <xref:System.Runtime.Serialization.SerializationInfo> obiektu o informacje o wyjątku.  (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Pobiera typ środowiska uruchomieniowego bieżącego wystąpienia. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Tworzy kopię pobieżną bieżącego obiektu. (Dziedziczone z <xref:System.Object>.)|  
|`public string ToString()`|Zwraca reprezentację ciągu bieżącego wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Zdarzenia  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Występuje, gdy wyjątek jest serializowany można utworzyć obiektu stanu wyjątek, który zawiera seryjnych danych o wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Szczegóły użycia  
 `MissingInteropDataException` Wyjątek podczas wywołania metody do składnika COM lub środowiska wykonawczego systemu Windows nie można wprowadzić pomyślnie, ponieważ informacje o typie nie jest dostępna.  
  
 Metadane, który jest dostępny dla aplikacji w czasie wykonywania jest definiowana za pomocą pliku dyrektyw (Konfiguracja XML) środowiska uruchomieniowego, *. rd.xml. Aby zapobiec zgłaszanie tego wyjątku w aplikacji, należy zmodyfikować ten plik, aby zdefiniować metadanych, które musi znajdować się w czasie wykonywania. Najczęściej, adres ten błąd, dodając `MarshalObject`, `MarshalDelegate`, lub `MarshalStructure` atrybutu element odpowiedniego programu w pliku dyrektyw środowiska uruchomieniowego. Aby uzyskać informacje o formacie tego pliku, zobacz [dyrektyw środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Ponieważ ten wyjątek wskazuje, że metadane wymagane przez aplikację nie jest dostępny w czasie wykonywania, nie powinien obsługiwać tego wyjątku w `try` / `catch` bloku. Należy zdiagnozować przyczyną wyjątku i usunięcia go przez dodanie odpowiedni wpis do pliku dyrektyw środowiska uruchomieniowego.  
  
 `MissingInteropDataException` Klasa zawiera składnik unikatowy pojedynczy `MissingType` właściwości, który wskazuje typ, którego metadane wymagane jest wywołanie metody powiodło się. Wszystkie pozostałe elementy członkowskie są dziedziczone z klasy podstawowej <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Exception?displayProperty=nameWithType>  
 [Klasa MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
