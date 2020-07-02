---
ms.openlocfilehash: 14585b6de3ce02884f8be789930fc8610f73ba7d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621265"
---
### <a name="horizontal-scrolling-and-virtualization"></a>Przewijanie w poziomie i Wirtualizacja

#### <a name="details"></a>Szczegóły

Ta zmiana ma zastosowanie do obiektu <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> , który wykonuje własną wirtualizację w kierunku prostopadłym do głównego kierunku przewijania (główny przykład to <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> EnableColumnVirtualization = &quot; true &quot; ).  Wynik niektórych operacji przewijania poziomego został zmieniony, aby generować wyniki, które są bardziej intuicyjne i bardziej podobne do wyników porównywalnych operacji wertykalnych.<p/>Operacje obejmują &quot; przewijanie tutaj &quot; i &quot; prawą krawędź &quot; , aby użyć nazw z menu dostępnego po kliknięciu prawym przyciskiem myszy poziomego paska przewijania.  Oba te obliczenia są przesunięte i wywoływane przez kandydata <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)> .<p/>Po przejściu do nowego przesunięcia &quot; można zmienić pojęcie tutaj &quot; lub &quot; prawej krawędzi, &quot; ponieważ nowa niezwirtualizowana zawartość zmieniła wartość <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> .<p/>Przed .NET Framework 4.6.2, operacja przewijania po prostu korzysta z przesunięcia kandydata, nawet jeśli nie jest to &quot; tutaj &quot; ani do &quot; prawej krawędzi &quot; .  Powoduje to &quot; odbijanie &quot; przycisku przewijania, najlepiej zilustrowanego na przykład. Załóżmy, że <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> ma ExtentWidth = 1000 i Width = 200.  Przewiń do &quot; prawej krawędzi &quot; używa przesunięcia kandydatów 1000-200 = 800.  Podczas przewijania do tego przesunięcia nowe kolumny są dezwirtualizowane. Załóżmy, że są one bardzo szerokie, tak aby zmiany zostały <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> wprowadzone do 2000.  Przewijanie zakończy się ciągiem HorizontalOffset = 800, a kciuk zostanie &quot; odbijać &quot; do bliskiej krawędzi paska przewijania — dokładnie o 800/2000 = 40%.<p/>Zmiana polega na ponownym obliczeniu nowego przesunięcia kandydata, gdy wystąpi taka sytuacja, i spróbuj ponownie. (Jak działa przewijanie w pionie). <p/>Ta zmiana zapewnia bardziej przewidywalne i intuicyjne środowisko użytkownika końcowego, ale może również mieć wpływ na dowolną aplikację, która zależy od dokładnej wartości <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=fullName> po przewinięciu w poziomie, niezależnie od tego, czy jest wywoływana przez użytkownika końcowego, czy przez jawne wywołanie <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)> .

#### <a name="suggestion"></a>Sugestia

Aplikacja, która używa przewidywanej wartości dla, <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=fullName> powinna zostać zmieniona w celu pobrania wartości rzeczywistej (i wartości <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> ) po dowolnym poziomie przewijania, który może ulec zmianie <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> z powodu cofnięcia wirtualizacji.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType></li></ul>|
