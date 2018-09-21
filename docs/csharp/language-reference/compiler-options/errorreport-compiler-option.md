---
title: -errorreport (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: dcbb9467da87a82147176bb0feb00383aff2c77f
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46561344"
---
# <a name="-errorreport-c-compiler-options"></a>-errorreport (opcje kompilatora C#)
Ta opcja zapewnia wygodny sposób, aby zgłosić błąd wewnętrzny kompilatora C# do firmy Microsoft.  
  
> [!NOTE]
>  W systemach Windows Vista i systemu Windows Server 2008 ustawienia raportowania błędów, które dla programu Visual Studio nie zastępują ustawienia wprowadzone za pośrednictwem raportowania błędów Windows (WER). Ustawienia raportowania błędów systemu Windows zawsze pierwszeństwo ustawienia raportowania błędów programu Visual Studio.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a>Argumenty  
 **Brak**  
 Raporty o błędach wewnętrznych kompilatora nie będą zbierane ani wysyłane do firmy Microsoft.  
  
 **wiersz**  
 Monituje o wysłanie raportu po pojawieniu się błędu wewnętrznego kompilatora. **wiersz** jest domyślną kolekcją podczas kompilowania aplikacji w środowisku programistycznym.  
  
 **kolejki**  
 Kolejkuje raport o błędach. Po zalogowaniu się przy użyciu poświadczeń administracyjnych może zgłaszać błędów od czasu ostatniego zalogowania się. Użytkownik nie jest monitowany o wysłanie raportu błędów więcej niż raz na trzy dni. **kolejka** jest domyślną kolekcją podczas kompilowania aplikacji w wierszu polecenia.  
  
 **Wyślij**  
 Automatycznie wysyła raporty błędów wewnętrznych kompilatora do firmy Microsoft. Aby włączyć tę opcję, musisz najpierw wyrazić zgodę na zasady zbierania danych firmy Microsoft. Po raz pierwszy należy określić **- errorreport: wysyłanie** na komputerze, wiadomość kompilatora odniesie Cię do witryny sieci Web, która zawiera zasady zbierania danych firmy Microsoft.  
    
## <a name="remarks"></a>Uwagi  
 Wewnętrzny błąd kompilatora (ICE) wyniki, gdy kompilator nie może przetworzyć pliku kodu źródłowego. W przypadku ICE kompilator nie generuje plik wyjściowy lub przydatne diagnostyki, która służy do poprawienia kodu.  
  
 W poprzednich wersjach po odebraniu ICE było zachęcani do skontaktuj się z pomocą techniczną firmy Microsoft, aby zgłosić problem. Za pomocą **- errorreport**, możesz podać informacje ICE do zespołu języka Visual C#. Twoje raporty o błędach może zwiększyć kompilatora w przyszłych wersjach.  
  
 Zdolność użytkownika do wysyłania raportów zależy od uprawnienia zasad komputera i użytkownika.  
  
 Aby uzyskać więcej informacji na temat debugera błędów zobacz [opis odzyskiwania po awarii. Watson dla narzędzia Windows (Drwtsn32.exe)](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony. Aby uzyskać więcej informacji, zobacz [Stroka kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Kliknij przycisk **kompilacji** stronę właściwości.  
  
3.  Kliknij przycisk **zaawansowane** przycisku.  
  
4.  Modyfikowanie **raportowanie wewnętrznych błędów kompilatora** właściwości.  
  
 Aby dowiedzieć się, jak programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
