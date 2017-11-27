---
title: /errorreport
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0abe276aaacdeb175c3af7067dffa81448450e22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="errorreport"></a>/errorreport
Określa sposób [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora Zgłoś wewnętrzne błędy kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja umożliwia dogodny do raportu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wewnętrzny błąd kompilatora (ICE) do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zespołu w firmie Microsoft. Domyślnie kompilator wysyła żadnych informacji do firmy Microsoft. Jednak jeśli wystąpi błąd wewnętrzny kompilatora, ta opcja umożliwia raportowanie błędów firmie Microsoft. Informacje te pomogą zidentyfikować przyczynę pracownicy firmy Microsoft i może zwiększyć kolejnej wersji programu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 Możliwość wysyłania raportów użytkownika zależy od uprawnień zasad komputera i użytkownika.  
  
 W poniższej tabeli przedstawiono wpływ `/errorreport` opcji.  
  
|Opcja|Zachowanie|  
|---|---|  
|`prompt`|Jeśli wystąpi błąd wewnętrzny kompilatora, okno dialogowe pojawia się, dzięki czemu można wyświetlić dokładne dane, które są zbierane przez kompilator. Można określić, czy istnieje żadnych poufnych informacji w raporcie o błędzie i podejmowania decyzji od tego, czy do wysłania do firmy Microsoft. Jeśli zdecydujesz się wysłać i umożliwienie ustawienia zasad komputera i użytkownika, kompilator wysyła dane do firmy Microsoft.|  
|`queue`|Kolejkuje raport o błędzie. Podczas logowania się z uprawnieniami administratora, od czasu ostatniego zalogowania w może raportować zakończą się niepowodzeniem (zostanie nie się monit o wysłanie raportu błędów więcej niż raz na trzy dni). Jest to domyślne zachowanie podczas `/errorreport` nie określono opcji.|  
|`send`|Jeśli wystąpi błąd wewnętrzny kompilatora i umożliwienie ustawienia zasad komputera i użytkownika, kompilator wysyła dane do firmy Microsoft.<br /><br /> Opcja `/errorReport:send` próbuje automatyczne wysyłanie informacji o błędach do firmy Microsoft. Ta opcja jest zależna od rejestru. Aby uzyskać więcej informacji na temat ustawiania odpowiednie wartości w rejestrze, zobacz [jak włączyć automatyczne raportowanie błędów w programie Visual Studio 2008 wiersza polecenia narzędzia](http://go.microsoft.com/fwlink/?LinkID=184695).|  
|`none`|Jeśli wystąpi błąd wewnętrzny kompilatora, go nie zostanie zbierane ani wysyłane do firmy Microsoft.|  
  
 Kompilator wysyła dane, które obejmuje stosu w momencie wystąpienia błędu, obejmujące niektóre kodu źródłowego. Jeśli `/errorreport` jest używany z [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opcji, a następnie wysłaniu całego pliku źródłowego.  
  
 Ta opcja jest optymalna dla [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opcja, ponieważ umożliwia pracownicy firmy Microsoft, aby łatwo odtwarzania błędu.  
  
> [!NOTE]
>  `/errorreport` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod próbuje skompilować `T2.vb`, jeśli kompilator napotkał błąd wewnętrzny kompilatora, monitów o wysłanie raportu o błędach do firmy Microsoft i.  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/ bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
