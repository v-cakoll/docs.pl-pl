---
title: Analizatory zabezpieczeń .NET - .NET
description: Używanie analizatorów zabezpieczeń .NET w pakiecie programu .NET Framework analizatorów znaleźć i zagrożenia bezpieczeństwa
author: billwagner
ms.author: billwagner
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 904218c177ea45f82a73b4532ce3230af954aa85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="the-net-framework-analyzer"></a>Analizator Framework .NET

Analizator Framework .NET umożliwia znaleźć potencjalnych problemów w kodzie aplikacji opartych na programie .NET Framework. Ta analizator znajduje potencjalne problemy, a także sugeruje rozwiązania ich.

Analizatora interaktywnie działa w programie Visual Studio podczas pisania kodu lub w ramach elementu konfiguracji kompilacji. Przy projektowaniu, należy dodać analizatora możliwie jak najszybciej do projektu. Wcześniej odnaleźć dotyczących potencjalnych problemów w kodzie, tym łatwiej są Aby rozwiązać problem. Jednak można go dodać w dowolnym momencie w cyklu programowania. Jego znajduje problemy z istniejącego kodu i ostrzeganie o nowe problemy, jak zachować opracowywania.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>Instalowanie i konfigurowanie analizatora .NET Framework

Analizatory zabezpieczeń .NET musi być zainstalowany jako pakietu NuGet, na każdy projekt, gdzie chcesz je uruchomić. Tylko jeden deweloper musi je dodać do projektu. Pakiet Analizator jest zależności projektu i zostanie uruchomiony na maszynie Każdy deweloper, gdy ma ona zaktualizowane rozwiązanie.

Analizator Framework .NET jest dostarczany w [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) pakietu NuGet. Ten pakiet zawiera określone analizatorów programu .NET Framework, w tym analizatorów zabezpieczeń. W większości przypadków należy [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) pakietu NuGet. Pakiet agregacji FxCopAnalyzers zawiera analizatorów framework zawarte w pakiecie Framework.Analyzers, jak również analizatory następujące:
- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): zawiera ogólne wskazówki i wskazówki dotyczące standardowych interfejsów API architektury .NET
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): zawiera analizatorów określonych do interfejsów API architektury .NET Core.
- [Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): znajdują się wskazówki dotyczące tekstu jako kod, w tym komentarzy.

Aby go zainstalować, kliknij prawym przyciskiem myszy projekt i wybierz pozycję "Zarządzaj zależności".
W Eksploratorze NuGet, wyszukaj "NetFramework analizator", lub jeśli wolisz "Fx Cop analizator". Zainstaluj najnowszą wersję stabilna ze wszystkich projektów w rozwiązaniu.

## <a name="using-the-net-framework-analyzer"></a>Za pomocą analizatora .NET Framework

Po zainstalowaniu pakietu NuGet, Skompiluj rozwiązanie. Analizatora będzie Zgłoś wszelkie problemy, które klient zlokalizuje baza kodu. Problemy są raportowane klientowi jako ostrzeżenia w oknie Lista błędów w usłudze Visual Studio, jak pokazano na poniższej ilustracji:

![problemy zgłoszone przez analizator framework](./media/framework-analyzers-2.png)

Podczas pisania kodu, zobaczysz zygzaki poniżej wszelkie potencjalne problemy w kodzie.
Umieść kursor nad jakikolwiek problem, i zobaczyć szczegółowe informacje o problemie i sugestie dotyczące wszystkie możliwe rozwiązanie, jak pokazano na poniższej ilustracji:

![interakcyjny raport problemów wykrytych przez analizatora framework](./media/framework-analyzers-1.png)

Analizatory badanie kodu w rozwiązaniu i udostępnić listę ostrzeżeń dla każdego z tych problemów:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy nie powinny rozszerzać pewnych typów bazowych

Istnieje niewielka liczba typów w programie .NET Framework należy nie pochodzi od bezpośrednio. 

**Kategoria:** projektu

**Ważność:** ostrzeżenie

Informacje dodatkowe: [CA:1058: typy nie powinny rozszerzać niektórych typów podstawowych](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: Nie Przechwytuj wyjątki uszkodzony

Połowowe wyjątki uszkodzony można zamaskować błędy (np. naruszenia zasad dostępu), co w stanie niespójnym wykonywania lub ułatwieniu osobom atakującym naruszyć bezpieczeństwo systemu. Zamiast tego catch i zajmują więcej określony zestaw typów wyjątków lub ponownie zgłosić wyjątek

**Kategoria:** zabezpieczeń

**Ważność:** ostrzeżenie

Informacje dodatkowe: [## CA2153: nie Przechwytuj wyjątki uszkodzony](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Należy zaimplementować konstruktory serializacji

Analizatora generuje ostrzeżenie podczas tworzenia typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu, ale nie definiuje konstruktora serializacji wymagane. Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony. Konstruktor serializacji ma następującą sygnaturą:

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

**Kategoria:** użycia

**Ważność:** ostrzeżenie

Informacje dodatkowe: [CA2229: zaimplementować konstruktory serializacji](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Należy oznaczyć wszystkie nieserializowane pola

Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji. To pole z jawnie należy oznaczyć <xref:System.NonSerializedAttribute> ustalenie to ostrzeżenie.

**Kategoria:** użycia

**Ważność:** ostrzeżenie

Informacje dodatkowe: [CA2235: oznaczyć wszystkie nieserializowane pola](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: Oznacz typy ISerializable z serializacji

Aby być rozpoznawane przez środowisko uruchomieniowe języka wspólnego jako możliwy do serializacji, typy muszą być oznaczone za pomocą <xref:System.SerializableAttribute> atrybutu nawet wtedy, gdy typ używa procedury niestandardowej serializacji zaimplementowanie <xref:System.Runtime.Serialization.ISerializable> interfejsu.

**Kategoria:** użycia

**Ważność:** ostrzeżenie

Informacje dodatkowe: [CA2237: Oznacz typy ISerializable atrybutem możliwy do serializacji](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: Przetwarzanie w kodzie XML definicji DTD niezabezpieczonych

Jeśli używasz niezabezpieczonych <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wystąpień lub odwołanie do zewnętrznej jednostki źródeł, analizator akceptuje niezaufanych argument wejściowy i argument wyjawiać poufnych informacji do osoby atakujące.  

**Kategoria:** zabezpieczeń

**Ważność:** ostrzeżenie

Informacje dodatkowe: [A3075: niebezpieczne DTD przetwarzania w kodzie XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)


### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nie używaj słabych algorytmów kryptograficznych

Algorytmy kryptograficzne zmniejsza się wraz z upływem czasu, jak ataki staną się bardziej zaawansowane. W zależności od typu i stosowania tego algorytmu kryptograficznego, dalsze pogorszenia się jego siły kryptograficznych może umożliwić atakującemu odczytywać wiadomości enciphered, manipulowanie enciphered wiadomości, forge podpisów cyfrowych, manipulowanie skrótu zawartości lub w przeciwnym razie złamania żadnych cryptosystem na podstawie tego algorytmu. Dla celów szyfrowania, przy użyciu algorytmu AES (AES 256, AES-192 i AES-128 są dozwolone) z kluczem o długości większej niż lub równy 128 bitów. Do tworzenia skrótów, użyj funkcji skrótu z rodziny SHA-2, np. 512 SHA-2, SHA-2 384 lub 256 SHA-2.

**Kategoria:** zabezpieczeń

**Ważność:** ostrzeżenie

Informacje dodatkowe: [CA5350: nie używaj słabych algorytmów kryptograficznych](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nie używaj przerwane algorytmy kryptograficzne

Istnieje ataku, dzięki czemu można przerwać ten algorytm wykonalne. Dzięki temu osoby atakujące przerwać gwarancje kryptograficznych, który ma na celu zapewnienie. W zależności od typu i stosowania tego algorytmu kryptograficznego to może umożliwić atakującemu odczytywać wiadomości enciphered, manipulowanie enciphered wiadomości, forge podpisów cyfrowych, manipulowanie skrótu zawartości lub w przeciwnym razie naruszenia żadnych cryptosystem na podstawie na tego algorytmu. Dla celów szyfrowania, przy użyciu algorytmu AES (AES 256, AES-192 i AES-128 są dozwolone) z kluczem o długości większej niż lub równy 128 bitów. Do tworzenia skrótów, użyj funkcji skrótu z rodziny SHA-2, takich jak SHA512, SHA384 i SHA256. W przypadku podpisów cyfrowych należy użyć RSA z kluczem o długości większa lub równa 2048 bitów lub ECDSA z kluczem o długości większej niż lub równa 256 bitów.

**Kategoria:** zabezpieczeń

**Ważność:** ostrzeżenie

Informacje dodatkowe: [CA5351: nie używaj przerwane algorytmy kryptograficzne](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)


