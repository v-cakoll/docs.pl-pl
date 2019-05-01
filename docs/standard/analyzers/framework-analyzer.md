---
title: Analizatory zabezpieczeń .NET — .NET
description: Dowiedz się, jak używane analizatory zabezpieczeń .NET pakietu .NET Framework analizatorów, aby zidentyfikować i rozwiązać zagrożenia bezpieczeństwa
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: cbd9bcdb12a423f54aa4ff82d88f07c20023c48f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947313"
---
# <a name="the-net-framework-analyzer"></a>Analizator struktury platformy .NET

Analizator struktury platformy .NET umożliwia znalezienie potencjalnych problemów w kodzie aplikacji opartych na programie .NET Framework. Ten analizatora umożliwia znalezienie potencjalnych problemów i sugeruje poprawki do nich.

Analizator działa interaktywnie w programie Visual Studio podczas pisania kodu lub jako część kompilacji ciągłej integracji. Tworzenie, należy dodać analizatora możliwie jak najszybciej do projektu. Szybciej znaleźć potencjalnych problemów w kodzie, tym łatwiej są Aby rozwiązać problem. Jednak można go dodać w dowolnym momencie w cyklu rozwoju. Znajdzie wszystkie problemy z istniejącego kodu i ostrzega o nowych problemach, jak zachować opracowywania.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>Instalowanie i konfigurowanie analizator struktury platformy .NET

Analizatory zabezpieczeń .NET musi być zainstalowany jako pakiet NuGet w projekcie, co potrzebne do uruchomienia. Tylko jeden deweloper musi zostać dodane do projektu. Pakiet analizatora jest zależnością projektu i zostanie uruchomiony na maszynie każdego dewelopera, gdy ma ona zaktualizowane rozwiązanie.

Analizator struktury platformy .NET jest dostarczany za [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) pakietu NuGet. Ten pakiet zawiera określone analizatory do programu .NET Framework, w tym analizatory zabezpieczeń. W większości przypadków należy [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) pakietu NuGet. Pakiet agregacji FxCopAnalyzers zawiera analizatorów framework zawarte w pakiecie Framework.Analyzers, jak również analizatory następujące:
- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Zawiera ogólne wskazówki i wskazówki dotyczące standardowych interfejsów API platformy .NET
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Zapewnia analizatory określonych interfejsów API platformy .NET Core.
- [Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Zawiera wskazówki dotyczące tekst zawarty jako kodu, w tym komentarzy.

Aby go zainstalować, kliknij prawym przyciskiem myszy nad projektem i wybierz pozycję "Zarządzaj zależności".
Z poziomu Eksploratora NuGet, wyszukaj "NetFramework analizatora", lub jeśli wolisz "Fx Cop analizatora". Zainstaluj najnowszą wersję stabilną we wszystkich projektach w rozwiązaniu.

## <a name="using-the-net-framework-analyzer"></a>Za pomocą analizatora .NET Framework

Po zainstalowaniu pakietu NuGet, Skompiluj rozwiązanie. Analizator będzie zgłaszać problemy, które klient zlokalizuje w bazie kodu. Problemy są zgłaszane jako ostrzeżenia w oknie Lista błędów w usłudze Visual Studio, jak pokazano na poniższej ilustracji:

![problemów zgłaszanych przez analizator struktury](./media/framework-analyzers-2.png)

Podczas pisania kodu, zobaczysz zygzaki poniżej potencjalne problemy w kodzie.
Umieść kursor nad dowolnym problemem i wyświetlić szczegółowe informacje o problemie i sugestie dotyczące wszystkie możliwe rozwiązanie, jak pokazano na poniższej ilustracji:

![interaktywny raport problemów wykrytych przez analizator struktury](./media/framework-analyzers-1.png)

Analizatorów sprawdzić kod w rozwiązaniu i udostępniać Ci listę ostrzeżeń dla każdego z tych problemów:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy nie powinny rozszerzać niektórych typów podstawowych

Istnieje niewielka liczba typów w .NET Framework, należy nie pochodzi od bezpośrednio. 

**Kategoria:** Projekt

**Ważność:** Ostrzeżenie

Informacje dodatkowe: [CA:1058: Typy nie powinny rozszerzać niektórych typów podstawowych](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: Nie przechwytuj wyjątki uszkodzony

Połowowe wyjątki uszkodzony może maskować błędów (np. naruszenia zasad dostępu), co w niespójnym stanie wykonywania lub ułatwianie dla osób atakujących do naruszenia bezpieczeństwa systemu. Zamiast tego catch i zajmują więcej określony zestaw typów wyjątków lub ponownie zgłosić wyjątek

**Kategoria:** Zabezpieczenia

**Ważność:** Ostrzeżenie

Informacje dodatkowe: [## CA2153: Nie przechwytuj wyjątki uszkodzony](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Zaimplementuj konstruktory serializacji

Analizator generuje to ostrzeżenie, po utworzeniu typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu, ale nie definiuje konstruktora serializacji wymagane. Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony. Konstruktor serializacji ma następujący podpis:

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

**Kategoria:** Użycie

**Ważność:** Ostrzeżenie

Informacje dodatkowe: [CA2229: Zaimplementuj konstruktory serializacji](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji

Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji. Musisz wyraźnie oznaczyć tego pola z <xref:System.NonSerializedAttribute> naprawić to ostrzeżenie.

**Kategoria:** Użycie

**Ważność:** Ostrzeżenie

Informacje dodatkowe: [CA2235: Oznacz wszystkie pola nieprzeznaczone do](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: Oznacz typy ISerializable atrybutem możliwy do serializacji

Aby zostały rozpoznane przez środowisko uruchomieniowe języka wspólnego jako możliwe do serializacji, typy muszą być oznaczone za pomocą <xref:System.SerializableAttribute> atrybutu nawet wtedy, gdy typ używa niestandardowych procedur serializacji przez zaimplementowanie <xref:System.Runtime.Serialization.ISerializable> interfejsu.

**Kategoria:** Użycie

**Ważność:** Ostrzeżenie

Informacje dodatkowe: [CA2237: Oznacz typy ISerializable atrybutem możliwy do serializacji](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: DTD niezabezpieczone przetwarzanie w formacie XML

Jeśli używasz niezabezpieczone <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wystąpień lub odwołanie do jednostki zewnętrznej źródeł, analizator może akceptować niezaufanych danych wejściowych i ujawnienia poufnych informacji dla osób atakujących.  

**Kategoria:** Zabezpieczenia

**Ważność:** Ostrzeżenie

Informacje dodatkowe: [A3075: DTD niezabezpieczone przetwarzanie w formacie XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nie używaj słabych algorytmów kryptograficznych

Algorytmy kryptograficzne zmniejsza się wraz z upływem czasu, jak ataki stają się bardziej zaawansowane. W zależności od typu i aplikacji to algorytmów kryptograficznych, dalsze degradacji jego sile szyfrowania może umożliwić atakującemu odczytywanie komunikatów z enciphered, manipulowanie enciphered wiadomości, forge podpisów cyfrowych, manipulowanie skrótu zawartości lub w przeciwnym razie naruszenia wszelkich cryptosystem, w oparciu o ten algorytm. Dla celów szyfrowania, Użyj algorytmu szyfrowania AES (AES-256, AES-192 i AES-128 są dopuszczalne) z kluczem o długości, większa niż lub równy 128 bitów. Do tworzenia skrótów, użyj funkcji skrótu z rodziny SHA-2, np. 512 SHA-2, SHA-2-384 lub 256 SHA-2.

**Kategoria:** Zabezpieczenia

**Ważność:** Ostrzeżenie

Informacje dodatkowe: [CA5350: Nie używaj słabych algorytmów kryptograficznych](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych

Istnieje atak, dzięki czemu można przerwać ten algorytm wykonalne. Pozwala to osobom atakującym przerwanie gwarancje kryptograficzne, które zaprojektowano w celu zapewnienia. W zależności od typu i aplikacji to algorytmów kryptograficznych to umożliwić osobom atakującym odczytywanie komunikatów z enciphered, manipulowanie enciphered wiadomości, forge podpisów cyfrowych, manipulowanie skrótu zawartości lub w przeciwnym razie naruszenia wszelkich cryptosystem na podstawie na ten algorytm. Dla celów szyfrowania, Użyj algorytmu szyfrowania AES (AES-256, AES-192 i AES-128 są dopuszczalne) z kluczem o długości, większa niż lub równy 128 bitów. Do tworzenia skrótów, użyj funkcji skrótu z rodziny SHA-2, takie jak SHA512, SHA384 lub SHA256. W przypadku podpisów cyfrowych za pomocą RSA z kluczem o długości, większa niż lub równa 2048 bitów lub ECDSA długość klucza jest większa niż lub równa 256 bitów.

**Kategoria:** Zabezpieczenia

**Ważność:** Ostrzeżenie

Aby uzyskać dodatkowe informacje: [CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)
