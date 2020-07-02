---
ms.openlocfilehash: eb89cbc72d8b09fd1aa5bc775a6c539eb208fa70
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614894"
---
### <a name="wpf-pointer-based-touch-stack"></a>Stos dotykowy oparty na wskaźnikach WPF

#### <a name="details"></a>Szczegóły

Ta zmiana umożliwia dodanie opcjonalnego stosu dotykowego i pióra WPF WM_POINTER.  Deweloperzy, którzy nie włączą jawnie tego, powinni zobaczyć, że nie zmienią się zachowania dotykowego i pióra WPF. Bieżące znane problemy z opcjonalnym stosem WM_POINTER i dotykiem piórem:

- Brak obsługi pisma odręcznego w czasie rzeczywistym.
- Podczas gdy narzędzia króla i StylusPlugIns — będą nadal działać, zostaną one przetworzone w wątku interfejsu użytkownika, co może prowadzić do słabej wydajności.
- Zmiany behawioralne spowodowane zmianami w trakcie podwyższania poziomu zdarzeń dotknięcia/piórem do zdarzeń myszy
- Manipulowanie może zachowywać się inaczej
- Operacja przeciągania/upuszczania nie pokazuje odpowiedniej opinii na temat wprowadzania dotykowego
- Nie ma to wpływu na wprowadzanie piórem
- Nie można już inicjować przeciągania/upuszczania w przypadku zdarzeń dotykowych/pióra
- Może to potencjalnie zawiesić aplikację, dopóki nie zostanie wykryta myszą.
- Zamiast tego deweloperzy powinni inicjować przeciąganie i upuszczanie ze zdarzeń myszy.

#### <a name="suggestion"></a>Sugestia

Deweloperzy, którzy chcą włączyć ten stos, mogą dodawać i scalać następujące elementy w pliku App.config aplikacji:

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Usunięcie tego lub ustawienie wartości false spowoduje wyłączenie tego opcjonalnego stosu. Należy zauważyć, że ten stos jest dostępny tylko w Update i nowszych wersjach systemu Windows 10.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4,7         |
| Typ    | Przekierowanie |
