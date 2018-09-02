---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d093b8ce4413a375e79eec239be37e83ac674d05
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417652"
---
# <a name="-errorreport"></a>-errorreport

Określa, jak kompilator języka Visual Basic powinno zgłosić wewnętrzne błędy kompilatora.

## <a name="syntax"></a>Składnia

```
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a>Uwagi

Ta opcja zapewnia wygodny sposób, aby zgłosić błąd wewnętrzny kompilatora Visual Basic (ICE) do zespołu języka Visual Basic w firmie Microsoft. Domyślnie kompilator wysyła żadnych informacji do firmy Microsoft. Jednak jeśli wystąpi błąd wewnętrzny kompilatora, ta opcja umożliwia raportowanie błędów firmie Microsoft. Te informacje pomagają inżynierów firmy Microsoft, zidentyfikować przyczynę i może poprawić kolejnej wersji programu Visual Basic.

Zdolność użytkownika do wysyłania raportów zależy od uprawnienia zasad komputera i użytkownika.

W poniższej tabeli przedstawiono efekt `-errorreport` opcji.

|Opcja|Zachowanie|
|---|---|
|`prompt`|Jeśli wystąpi błąd wewnętrzny kompilatora, okno dialogowe funkcjonuje tak, aby wyświetlić dokładnych danych zebranych przez kompilator. Można określić, czy ma żadnych poufnych informacji w raporcie o błędach i decyzji od tego, czy wysyłać je do firmy Microsoft. Jeśli zdecydujesz się wysłać go i zezwalają na to ustawienia zasad komputera i użytkownika, kompilator wysyła dane do firmy Microsoft.|
|`queue`|Kolejkuje raport o błędach. Po zalogowaniu się przy użyciu uprawnień administratora, możesz zgłaszać błędów od czasu ostatniego zostały zarejestrowane w (użytkownik nie jest monitowany o wysłanie raportu błędów więcej niż raz na trzy dni). Jest to domyślne zachowanie podczas `-errorreport` opcja nie jest określona.|
|`send`|Jeśli wystąpi błąd wewnętrzny kompilatora i zezwalają na to ustawienia zasad komputera i użytkownika, kompilator wysyła dane do firmy Microsoft.<br /><br /> Opcja `-errorreport:send` próbuje automatycznie wysyłać informacje o błędach do firmy Microsoft, jeśli raportowania został włączony przez [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) ustawienia systemu. |
|`none`|Jeśli wystąpi błąd wewnętrzny kompilatora, go będzie nie być zbierane lub wysyłane do firmy Microsoft.|

Kompilator wysyła dane, która zawiera stos w momencie wystąpienia błędu, który zwykle zawiera niektóre kody źródłowe. Jeśli `-errorreport` jest używana z [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opcji, a następnie wysłaniu całego pliku źródłowego.

Ta opcja jest optymalna dla [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opcji, ponieważ zezwala ona na inżynierów firmy Microsoft, aby łatwo odtworzyć błąd.

> [!NOTE]
> `-errorreport` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.

## <a name="example"></a>Przykład

Poniższy kod próbuje skompilować `T2.vb`, i gdy kompilator napotka błąd wewnętrzny kompilatora, jednak monituje o wysłanie raportu o błędach do firmy Microsoft.

```
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
