---
title: -errorreport (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
caps.latest.revision: "35"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3063a29452d90a09d5904d2a598b62530104d739
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="errorreport-c-compiler-options"></a>/errorreport (opcje kompilatora C#)
Ta opcja zapewnia wygodny sposób, aby zgłosić błąd wewnętrzny kompilatora C# do firmy Microsoft.  
  
> [!NOTE]
>  Ustawienia raportowania błędów powodujących, że dla programu Visual Studio nie zastępują ustawienia wprowadzone za pośrednictwem raportowania błędów systemu Windows (WER) w systemie Windows Vista i Windows Server 2008. Ustawienia raportowania błędów systemu Windows zawsze pierwszeństwo ustawienia raportowania błędów programu Visual Studio.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a>Argumenty  
 **Brak**  
 Raporty o błędach wewnętrznych kompilatora nie będą zbierane lub wysyłane do firmy Microsoft.  
  
 **wiersz**  
 Monituje o wysłanie raportu po pojawieniu się błędu wewnętrznego kompilatora. **wiersz** jest domyślną kolekcją podczas kompilowania aplikacji w środowisku programistycznym.  
  
 **kolejki**  
 Kolejkuje raport o błędzie. Po zalogowaniu się przy użyciu poświadczeń administracyjnych, od czasu ostatniego zalogowania się może raportować zakończą się niepowodzeniem. Możesz nie będzie proszony o wysłanie raportu błędów więcej niż raz na trzy dni. **kolejka** jest domyślną kolekcją podczas kompilowania aplikacji w wierszu polecenia.  
  
 **Wyślij**  
 Automatycznie wysyła raporty błędów wewnętrznych kompilatora do firmy Microsoft. Aby włączyć tę opcję, należy najpierw wyrazić zgodę na zasady gromadzenia danych firmy Microsoft. Należy określić po raz pierwszy **/errorreport: Send** na komputerze, wiadomość kompilatora odniesie Cię do witryny sieci Web, który zawiera zasady zbierania danych firmy Microsoft.  
    
## <a name="remarks"></a>Uwagi  
 Wewnętrzny błąd kompilatora (ICE) powoduje, gdy kompilator nie może przetworzyć pliku kodu źródłowego. W przypadku ICE kompilator nie tworzy pliku wyjściowego lub żadnych przydatne diagnostyki, którego można użyć, aby naprawić kod.  
  
 W poprzednich wersjach po odebraniu ICE było zaleca się z pomocą techniczną firmy Microsoft, aby zgłosić problem. Za pomocą **/errorreport**, możesz podać informacje ICE do zespołu Visual C#. Z raportów o błędach może zwiększyć kompilatora w przyszłych wersjach.  
  
 Możliwość wysyłania raportów użytkownika zależy od uprawnień zasad komputera i użytkownika.  
  
 Aby uzyskać więcej informacji na temat debuger błędów zobacz [opis odzyskiwania po awarii. Watson dla narzędzi systemu Windows (Drwtsn32.exe)](http://go.microsoft.com/fwlink/?LinkId=147286).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony. Aby uzyskać więcej informacji, zobacz [strona kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Kliknij przycisk **zaawansowane** przycisku.  
  
4.  Modyfikowanie **raportowanie wewnętrznych błędów kompilatora** właściwości.  
  
 Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
