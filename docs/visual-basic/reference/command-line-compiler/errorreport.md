---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: a9741f7a8283f8603e02dae5abea151c6ee5d75e
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775668"
---
# <a name="-errorreport"></a>-errorreport

Określa sposób, w jaki kompilator Visual Basic powinien raportować wewnętrzne błędy kompilatora.

## <a name="syntax"></a>Składnia

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a>Uwagi

Ta opcja zapewnia wygodny sposób raportowania Visual Basic wewnętrznego błędu kompilatora (lodem) do zespołu Visual Basic w firmie Microsoft. Domyślnie kompilator nie wysyła żadnych informacji do firmy Microsoft. Jeśli jednak wystąpi błąd wewnętrzny kompilatora, ta opcja pozwala zgłosić błąd do firmy Microsoft. Te informacje ułatwią inżynierom firmy Microsoft Identyfikowanie przyczyny i mogą pomóc w ulepszaniu kolejnej wersji Visual Basic.

Możliwość wysyłania raportów przez użytkownika zależy od uprawnień zasad komputera i użytkownika.

Poniższa tabela zawiera podsumowanie wpływu opcji `-errorreport`.

|Opcja|Zachowanie|
|---|---|
|`prompt`|Jeśli wystąpi wewnętrzny błąd kompilatora, pojawi się okno dialogowe, które umożliwia wyświetlenie dokładnych danych zebranych przez kompilator. Można określić, czy w raporcie o błędach znajdują się informacje poufne i podjąć decyzję o tym, czy wysłać ją do firmy Microsoft. Jeśli użytkownik zdecyduje się ją wysłać, a ustawienia zasad komputera i użytkownika zezwalają na to, kompilator wysyła dane do firmy Microsoft.|
|`queue`|Kolejkuje raport o błędach. Gdy logujesz się przy użyciu uprawnień administratora, możesz zgłosić błędy od momentu ostatniego logowania (nie będzie wyświetlany monit o wysłanie raportów dla błędów więcej niż raz na trzy dni). Jest to zachowanie domyślne, gdy opcja `-errorreport` nie została określona.|
|`send`|Jeśli wystąpi wewnętrzny błąd kompilatora, a ustawienia zasad komputera i użytkownika zezwalają na to, kompilator wysyła dane do firmy Microsoft.<br /><br /> Opcja `-errorreport:send` próbuje automatycznie wysłać informacje o błędzie do firmy Microsoft, jeśli raportowanie jest włączone przez ustawienia systemu [raportowanie błędów systemu Windows](/windows/desktop/wer/windows-error-reporting) . |
|`none`|W przypadku wystąpienia wewnętrznego błędu kompilatora nie będzie on zbierany ani wysyłany do firmy Microsoft.|

Kompilator wysyła dane, które obejmują stos w momencie błędu, co zwykle zawiera kod źródłowy. Jeśli `-errorreport` jest używany z opcją [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) , zostanie wysłany cały plik źródłowy.

Ta opcja jest najlepiej używana z opcją [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) , ponieważ umożliwia inżynierom firmy Microsoft łatwiejsze odtwarzanie błędu.

> [!NOTE]
> Opcja `-errorreport` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.

## <a name="example"></a>Przykład

Poniższy kod próbuje skompilować `T2.vb`, a jeśli kompilator napotyka wewnętrzny błąd kompilatora, zostanie wyświetlony komunikat z prośbą o wysłanie raportu o błędach do firmy Microsoft.

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
