---
ms.openlocfilehash: 9659068304eb208fd6a0a753273453bc669fbc56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621274"
---
### <a name="keytips-behavior-improved-in-wpf"></a>Ulepszone zachowanie podpowiedzi w WPF

#### <a name="details"></a>Szczegóły

W celu zachowania zgodności z zachowaniem programu Microsoft Word i Eksploratora Windows należy zmodyfikować zachowanie podpowiedzi. Sprawdzając, czy stan poradę dotyczącą klawiszy jest włączony lub nie jest w przypadku <xref:System.Windows.Input.KeyEventArgs.SystemKey> naciśnięcia (w szczególności <xref:System.Windows.Input.Key> lub <xref:System.Windows.Input.Key.F11> ), WPF odpowiednio obsługuje klucze poradę dotyczącą klawiszy. Porady dotyczące klawisza umożliwiają teraz odrzucanie menu nawet wtedy, gdy jest ono otwierane za pomocą myszy.

#### <a name="suggestion"></a>Sugestia

Nie dotyczy

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|
