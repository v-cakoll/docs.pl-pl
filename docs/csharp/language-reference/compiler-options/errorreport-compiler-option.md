---
title: -errorreport (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 52b58aac5e82d4228dfda9c4d77c1d1c5de3e0cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253892"
---
# <a name="-errorreport-c-compiler-options"></a>-errorreport (Opcje kompilatora C#)
Ta opcja zapewnia wygodny sposób zgłaszania błędu kompilatora wewnętrznego języka C# do firmy Microsoft.

> [!NOTE]
> W systemach Windows Vista i Windows Server 2008 ustawienia raportowania błędów wprowadzone w programie Visual Studio nie zastępują ustawień dokonanych za pomocą raportowania błędów systemu Windows (WER). Ustawienia wer zawsze mają pierwszeństwo przed ustawieniami raportowania błędów programu Visual Studio.

## <a name="syntax"></a>Składnia

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a>Argumenty
 **brak**  
 Raporty dotyczące błędów wewnętrznego kompilatora nie będą zbierane ani wysyłane do firmy Microsoft.

 **monit** Monituje o wysłanie raportu po otrzymaniu wewnętrznego błędu kompilatora. **monit** jest domyślnym podczas kompilowania aplikacji w środowisku programistycznym.

 **kolejka** Kolejkuje raport o błędach. Po zalogowaniu się przy użyciu poświadczeń administracyjnych można zgłaszać wszelkie błędy od czasu ostatniego logowania. Nie będzie wyświetlany monit o wysyłanie raportów o błędach więcej niż raz na trzy dni. **kolejka** jest domyślna podczas kompilowania aplikacji w wierszu polecenia.

 **wyślij** Automatycznie wysyła raporty o wewnętrznych błędach kompilatora do firmy Microsoft. Aby włączyć tę opcję, należy najpierw wyrazić zgodę na zasady zbierania danych firmy Microsoft. Przy pierwszym określeniu **-errorreport:send** na komputerze komunikat kompilatora będzie odwoływać się do witryny sieci Web zawierającej zasady zbierania danych firmy Microsoft.

## <a name="remarks"></a>Uwagi
 Wewnętrzny błąd kompilatora (ICE) wyniki, gdy kompilator nie może przetworzyć pliku kodu źródłowego. Gdy wystąpi ICE, kompilator nie generuje pliku wyjściowego lub żadnych przydatnych diagnostycznych, które można użyć do naprawy kodu.

 W poprzednich wersjach po otrzymaniu urządzenia ICE zachęcano do skontaktowania się z pomocą techniczną firmy Microsoft w celu zgłoszenia problemu. Za pomocą **-errorreport**, można podać informacje ICE do zespołu Visual C#. Raporty o błędach mogą pomóc w ulepszeniu przyszłych wersji kompilatora.

 Możliwość wysyłania raportów przez użytkownika zależy od uprawnień do obsługi zasad komputera i użytkownika.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz stronę **Właściwości** projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie strony, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).

2. Kliknij stronę **Właściwości kompilacji.**

3. Kliknij przycisk **Zaawansowane.**

4. Zmodyfikuj właściwość **Raportowanie błędów kompilatora wewnętrznego.**

 Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>opcji kompilatora, zobacz .

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
