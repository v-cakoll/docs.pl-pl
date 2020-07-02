---
ms.openlocfilehash: 5e2e8d1ec5d698d1c1649c2a0a1b4b77dbdf4022
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621277"
---
### <a name="wpf-printing-stack-update"></a>Aktualizacja stosu drukowania WPF

#### <a name="details"></a>Szczegóły

Interfejsy API drukowania platformy WPF korzystające z <xref:System.Printing.PrintQueue?displayProperty=fullName> interfejsu API Wywołaj teraz okna wywołującego na rzecz obecnie przestarzałego interfejsu API drukowania XPS. Zmiany zostały wprowadzone z myślą o potrzebach. ani użytkownicy, ani deweloperzy nie powinni widzieć żadnych zmian w zachowaniu lub użyciu interfejsu API. Nowy stos drukowania jest domyślnie włączony podczas uruchamiania aktualizacji systemu Windows 10 dla twórców. Stary stos drukowania nadal będzie działać tak samo jak wcześniej w starszych wersjach systemu Windows.

#### <a name="suggestion"></a>Sugestia

Aby użyć starego stosu w aktualizacji systemu Windows 10 dla twórców, należy ustawić <code>UseXpsOMPrinting</code> wartość REG_DWORD <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> klucza rejestru na <code>1</code> .

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4,7|
|Typ|Środowisko uruchomieniowe|
