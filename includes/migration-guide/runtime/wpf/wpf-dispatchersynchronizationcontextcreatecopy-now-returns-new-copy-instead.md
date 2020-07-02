---
ms.openlocfilehash: fc6066fd0b23d299158114cb397934041b99ba47
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620465"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>Funkcja WPF DispatcherSynchronizationContext. setcopy zwraca teraz nową kopię zamiast bieżącego wystąpienia

#### <a name="details"></a>Szczegóły

W .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> zwrócił odwołanie do bieżącego wystąpienia, głównie jako Optymalizacja wydajności. W .NET Framework 4,5 zwraca nowe wystąpienie, które umożliwia po raz pierwszy zawrzeć te same odwołania wskazujące wykonywany wątek znajduje się w poprawnym kontekście synchronizacji.  Jest mało prawdopodobne, że kod, który sprawdza tożsamość tych odwołań, będzie dotyczył, ale ze względu na zmianę, kod, który wywołuje, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> powinien być testowany w ramach migracji do .NET Framework 4,5 lub nowszego.

#### <a name="suggestion"></a>Sugestia

Należy pamiętać, że <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> program zwróci teraz nowy <xref:System.Threading.SynchronizationContext?displayProperty=fullName> obiekt. Wcześniej kod, który używał równoważności odwołań, wygenerował w ten sposób, nie sprawdza, czy znajdował się w odpowiednim kontekście, ale jest zbudowany w oparciu o .NET Framework 4,5 lub nowszy.  Chociaż mało prawdopodobne, aby powodować problemy, wykonywanie odpowiednich ścieżek kodu powinno być wystarczające, aby określić, czy stanowi to problem.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
