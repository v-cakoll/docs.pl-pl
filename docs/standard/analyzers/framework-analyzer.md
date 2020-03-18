---
title: Analizatory .NET Framework — .NET
description: Dowiedz się, jak używać analizatorów .NET Framework w pakiecie analizatorów .NET Framework do znajdowania i eliminowania zagrożeń bezpieczeństwa
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: dd69671e709549fe0ad0f582e4d09b43f7321df2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156000"
---
# <a name="the-net-framework-analyzer"></a>Analizator platformy .NET Framework

Za pomocą analizatora .NET Framework można znaleźć potencjalne problemy w kodzie aplikacji opartym na platformie .NET Framework. Ten analizator znajduje potencjalne problemy i sugeruje poprawki do nich.

Analizator działa interaktywnie w programie Visual Studio podczas pisania kodu lub jako część kompilacji ci. Należy dodać analizator do projektu tak wcześnie, jak to możliwe w rozwoju. Im szybciej znajdziesz jakieś potencjalne problemy w kodzie, tym łatwiej je naprawić. Jednak można dodać go w dowolnym momencie w cyklu rozwoju. Znajduje żadnych problemów z istniejącym kodem i ostrzega o nowych problemów podczas dalszego opracowywania.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>Instalowanie i konfigurowanie analizatora programu .NET Framework

Analizatory .NET Framework muszą być zainstalowane jako pakiet NuGet w każdym projekcie, w którym mają być uruchamiane. Tylko jeden deweloper musi dodać je do projektu. Pakiet analizatora jest zależnością projektu i będzie uruchamiany na komputerze każdego dewelopera, gdy ma zaktualizowane rozwiązanie.

Analizator platformy .NET Framework jest dostarczany w pakiecie [NuGet programu Microsoft.NetFramework.Analyzers.](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) Ten pakiet zawiera tylko analizatory specyficzne dla .NET Framework, który zawiera analizatory zabezpieczeń. W większości przypadków należy [microsoft.codeanalysis.fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) nuget pakietu.
Pakiet zbiorczy FxCopAnalyzers zawiera wszystkie analizatory framework zawarte w pakiecie Framework.Analyzers, a także następujące analizatory:

- [Microsoft.CodeQuality.Analyzeers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Zawiera ogólne wskazówki i wskazówki dotyczące standardowych interfejsów API platformy .NET
- [Microsoft.NetCore.Analyzeers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Udostępnia analizatory specyficzne dla interfejsów API .NET Core.
- [Text.Analyzeers](https://www.nuget.org/packages/Text.Analyzers): Zawiera wskazówki dotyczące tekstu dołączonego jako kod, w tym komentarzy.

Aby go zainstalować, kliknij prawym przyciskiem myszy projekt i wybierz polecenie "Zarządzaj zależnościami".
Z nuget explorer, wyszukaj "NetFramework Analyzer", lub jeśli wolisz, "Fx Cop Analyzer". Zainstaluj najnowszą stabilną wersję we wszystkich projektach w rozwiązaniu.

## <a name="using-the-net-framework-analyzer"></a>Korzystanie z analizatora programu .NET Framework

Po zainstalowaniu pakietu NuGet skompiluj rozwiązanie. Analizator zgłosi wszelkie problemy, które lokalizuje w bazie kodu. Problemy są zgłaszane jako ostrzeżenia w oknie Lista błędów programu Visual Studio, jak pokazano na poniższym obrazie:

![problemy zgłaszane przez analizator ram](./media/framework-analyzers-2.png)

Podczas pisania kodu, zobaczysz squiggles pod wszelkie potencjalne problem w kodzie.
Umieść wskaźnik myszy na dowolnym problemie, a zobaczysz szczegóły dotyczące problemu oraz sugestie dotyczące wszelkich możliwych poprawek, jak pokazano na poniższym obrazku:

![interaktywny raport o problemach wykrytych przez analizator ram](./media/framework-analyzers-1.png)

Analizatory zbadać kod w rozwiązaniu i zapewnić listę ostrzeżeń dla każdego z tych problemów:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy nie powinny rozszerzać pewnych typów bazowych

Istnieje niewielka liczba typów w .NET Framework, które nie powinny pochodzić bezpośrednio.

**Kategoria:** Projektowania

**Ważność:** ostrzeżenie

Dodatkowe informacje: [CA:1058: Typy nie powinny rozszerzać niektórych typów podstawowych](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: Nie wychwytuj wyjątków stanu uszkodzonego

Przechwytywanie wyjątków stanu uszkodzonego może maskować błędy (takie jak naruszenia dostępu), co powoduje niespójny stan wykonania lub ułatwia niebezpieczeństwo naruszenia systemu. Zamiast tego złapać i obsługiwać bardziej szczegółowy zestaw typów wyjątków lub ponownie zgłosić wyjątek

**Kategoria:** Zabezpieczeń

**Ważność:** ostrzeżenie

Dodatkowe informacje: [## CA2153: Nie wyłapuj wyjątków stanu uszkodzonego](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Należy zaimplementować konstruktory serializacji

Analizator generuje to ostrzeżenie podczas tworzenia typu, <xref:System.Runtime.Serialization.ISerializable> który implementuje interfejs, ale nie definiuje wymagany konstruktor serializacji. Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony. Konstruktor serializacji ma następujący podpis:

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

**Kategoria:** Użycia

**Ważność:** ostrzeżenie

Dodatkowe informacje: [CA2229: Implementowanie konstruktorów serializacji](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Należy oznaczyć wszystkie nieserializowane pola

Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji. Należy jawnie oznaczyć <xref:System.NonSerializedAttribute> to pole, aby naprawić to ostrzeżenie.

**Kategoria:** Użycia

**Ważność:** ostrzeżenie

Dodatkowe informacje: [CA2235: Oznacz wszystkie pola niepodlegające serializacji](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: Mark ISerializable typy z serializable

Aby być rozpoznawanym przez program runtime języka wspólnego jako <xref:System.SerializableAttribute> serializable, typy muszą być oznaczone <xref:System.Runtime.Serialization.ISerializable> przy użyciu atrybutu, nawet wtedy, gdy typ używa niestandardowej procedury serializacji przez implementowanie interfejsu.

**Kategoria:** Użycia

**Ważność:** ostrzeżenie

Dodatkowe informacje: [CA2237: Mark ISerializable typy z serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: Niezabezpieczone przetwarzanie DTD w xml

Jeśli używasz niezabezpieczonych <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wystąpień lub odwołujesz się do zewnętrznych źródeł encji, analizator może akceptować niezaufane dane wejściowe i ujawniać poufne informacje osobom atakującym.  

**Kategoria:** Zabezpieczeń

**Ważność:** ostrzeżenie

Dodatkowe informacje: [A3075: Niezabezpieczone przetwarzanie DTD w xml](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nie używaj słabych algorytmów kryptograficznych

Algorytmy kryptograficzne ulegają degradacji w miarę postępów ataków. W zależności od typu i zastosowania tego algorytmu kryptograficznego dalsza degradacja jego siły kryptograficznej może umożliwić napastnikom odczytywanie zaszyfrowanych wiadomości, manipulowanie zaszyfrowanymi wiadomościami, fałszowanie podpisów cyfrowych, manipulowanie haszowanymi treściami lub w przeciwnym razie naruszyć wszelkie kryptosystem oparty na tym algorytmie. W przypadku szyfrowania należy użyć algorytmu AES (Dopuszczalne są AES-256, AES-192 i AES-128) o długości klucza większej lub równej 128 bitom. W przypadku mieszania należy użyć funkcji mieszania w rodzinie SHA-2, takiej jak SHA-2 512, SHA-2 384 lub SHA-2 256.

**Kategoria:** Zabezpieczeń

**Ważność:** ostrzeżenie

Dodatkowe informacje: [CA5350: Nie używaj słabych algorytmów kryptograficznych](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych

Istnieje atak, dzięki czemu możliwe jest obliczenia, aby złamać ten algorytm. Dzięki temu osoby atakujące mogą złamać gwarancje kryptograficzne, które ma zapewnić. W zależności od typu i zastosowania tego algorytmu kryptograficznego może to umożliwić osobom atakującym odczytywanie zaszyfrowanych wiadomości, manipulowanie zaszyfrowanymi wiadomościami, fałszowanie podpisów cyfrowych, manipulowanie haszowanymi treściami lub w inny sposób narażanie na szwank dowolnego opartego na systemie kryptograficznym na tym algorytmie. W przypadku szyfrowania należy użyć algorytmu AES (Dopuszczalne są AES-256, AES-192 i AES-128) o długości klucza większej lub równej 128 bitom. W przypadku mieszania należy użyć funkcji mieszania w rodzinie SHA-2, takiej jak SHA512, SHA384 lub SHA256. W przypadku podpisów cyfrowych należy używać rsa o długości klucza większej lub równej 2048 bitom lub ECDSA o długości klucza większej lub równej 256 bitom.

**Kategoria:** Zabezpieczeń

**Ważność:** ostrzeżenie

Dodatkowe informacje: [CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych](/visualstudio/code-quality/ca5351)
