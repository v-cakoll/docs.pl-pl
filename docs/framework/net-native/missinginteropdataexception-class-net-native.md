---
title: Klasa MissingInteropDataException (architektura .NET Native)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31208a63caaf9158f12742f1547b0e1e2781de4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866889"
---
# <a name="missinginteropdataexception-class-net-native"></a>Klasa MissingInteropDataException (architektura .NET Native)
**Platforma .NET dla aplikacji Windows dla systemu Windows 10, [!INCLUDE[net_native](../../../includes/net-native-md.md)] tylko**  
  
 Wyjątek, który jest zgłaszany, gdy ręcznego marshaling metoda jest wywoływana, ale metadanych dla typu nie zostanie odnaleziony przez analizę statyczną lub w pliku dyrektyw środowiska uruchomieniowego.  
  
 **Namespace:** System.Runtime.CompilerServices  
  
> [!IMPORTANT]
>  `MissingInteropDataException` Klasa jest przeznaczona wyłącznie do użytku wewnętrznego w [!INCLUDE[net_native](../../../includes/net-native-md.md)] łańcucha narzędzi. Nie jest przeznaczony do użycia w kodzie innych firm, nie powinien obsługiwać wyjątek w kodzie aplikacji. Zamiast tego wyjątku można wyeliminować, dodając wpisów, aby Twoje [plik dyrektywy środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
## <a name="syntax"></a>Składnia  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 `MissingInteropDataException` Klasy ma następujące składowe:  
  
## <a name="constructors"></a>Konstruktorów  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|Inicjuje nowe wystąpienie klasy `MissingInteropDataException` klasy za pomocą Identyfikatora dostarczane przez system komunikatu, który opisuje błąd i typu danych, których brakuje. Ten konstruktor jest do użytku wewnętrznego przez [!INCLUDE[net_native](../../../includes/net-native-md.md)] tylko łańcucha narzędzi.|  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Pobiera kolekcję par klucz/wartość, które zawierają dodatkowe informacje zdefiniowane przez użytkownika o wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Pobiera lub ustawia łącze, aby plik pomocy skojarzony z tym wyjątkiem. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Pobiera lub ustawia `HRESULT`, który jest kodowany wartość liczbowa, która jest przypisana do określonego wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Pobiera wyjątek, który spowodował bieżący wyjątek. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Pobiera komunikat, który opisuje bieżący wyjątek. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type MissingType { get; private set; }`|Pobiera lub ustawia typ danych, których nie istnieje.|  
|`public string Source { get; set; }`|Pobiera lub ustawia nazwę aplikacji lub obiekt, który spowodował błąd. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Pobiera reprezentację ciągu natychmiastowego ramek na stosie wywołań. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Pobiera metodę, która zgłosiła wyjątek bieżący. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Określa, czy określony obiekt jest równy bieżącemu obiektowi.  (Dziedziczone z <xref:System.Object>.)|  
|`protected void Finalize()`|Umożliwia obiektu spróbuj zwolnić zasoby i wykonywać inne operacje oczyszczania, zanim go jest odzyskiwane przez wyrzucanie elementów bezużytecznych. (Dziedziczone z <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Zwraca wyjątek, który jest główną przyczynę jeden lub kilka kolejnych wyjątków. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Zwraca wartość skrótu dla `MissingInteropDataException` wystąpienia.   (Dziedziczone z <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Zestawy <xref:System.Runtime.Serialization.SerializationInfo> obiektów z informacją o wyjątku.  (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Pobiera typ środowiska uruchomieniowego bieżącego wystąpienia. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Tworzy płytką kopię bieżącego obiektu. (Dziedziczone z <xref:System.Object>.)|  
|`public string ToString()`|Zwraca reprezentację ciągu bieżącego wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Zdarzenia  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Występuje, gdy wyjątek jest serializowana. Aby utworzyć obiekt stan wyjątku, który zawiera serializowane dane o wyjątku. (Dziedziczone z <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Szczegóły użycia  
 `MissingInteropDataException` Wyjątek jest zgłaszany, gdy wywołanie metody do składnika modelu COM lub środowisko uruchomieniowe Windows nie można przeprowadzić pomyślnie, ponieważ informacje o typie nie jest dostępna.  
  
 Metadane, który jest dostępny do aplikacji w czasie wykonywania jest definiowany przez plik dyrektywy (Konfiguracja XML) środowiska uruchomieniowego, *. rd.xml. Aby zapobiec sytuacji, w której aplikacja zostanie zgłoszony wyjątek, należy zmodyfikować ten plik, aby zdefiniować metadane, które musi znajdować się w czasie wykonywania. Najczęściej, adres ten błąd, dodając `MarshalObject`, `MarshalDelegate`, lub `MarshalStructure` atrybutu do elementu odpowiedniego programu w pliku dyrektyw środowiska uruchomieniowego. Aby uzyskać informacje o formacie pliku, zobacz [dyrektywy środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Ponieważ ten wyjątek wskazuje, że metadane wymagane przez aplikację nie jest dostępna w czasie wykonywania, nie powinien obsługiwać tego wyjątku w `try` / `catch` bloku. Zamiast tego należy przyczynę wyjątku i wyeliminuj je, dodając odpowiedni wpis do pliku dyrektyw środowiska uruchomieniowego.  
  
 `MissingInteropDataException` Klasa zawiera jeden element członkowski unikatowy, `MissingType` właściwości, który wskazuje na typ, którego metadanych jest wymagany w przypadku wywołania metody pomyślnie. Wszystkie pozostałe elementy członkowskie są dziedziczone z klasy bazowej <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Exception?displayProperty=nameWithType>
- [Klasa MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
