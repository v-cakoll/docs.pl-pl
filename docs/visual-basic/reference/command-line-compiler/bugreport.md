---
title: /bugreport
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7090142f940ae42f554fc0ba16bcc80d8537e38a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="bugreport"></a>/bugreport
Tworzy plik, który można używać podczas pliku raport o usterce.  
  
## <a name="syntax"></a>Składnia  
  
```  
/bugreport:file  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`file`|Wymagany. Nazwa pliku, który będzie zawierać raport o usterce. Nazwę pliku należy ująć w cudzysłów (""), jeśli nazwa zawiera spację.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące informacje są dodawane do `file`:  
  
-   Kopiowanie wszystkich plików kodu źródłowego w kompilacji.  
  
-   Listy opcji kompilatora używane w kompilacji.  
  
-   Informacje o wersji o kompilatora, środowisko uruchomieniowe języka wspólnego i systemu operacyjnego.  
  
-   Kompilator output, jeśli istnieje.  
  
-   Opis problemu, dla którego zostanie wyświetlony monit.  
  
-   Opis sposobu uważasz, że problem należy ustalić, dla którego zostanie wyświetlony monit.  
  
 Ponieważ kopię wszystkich plików kodu źródłowego znajduje się w `file`, może zajść potrzeba kodu (podejrzanych) wada najkrótszy program można odtworzyć.  
  
> [!IMPORTANT]
>  `/bugreport` Opcja tworzy plik zawierający potencjalnie wrażliwe informacje. Obejmuje to bieżący czas, wersja kompilatora [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] wersji, wersja systemu operacyjnego, nazwa użytkownika, argumenty wiersza polecenia, z którymi uruchamiania kompilatora, całego kodu źródłowego i forma binarna wszelkie odwołania do zestawu. Ta opcja jest dostępny przez określenie opcji wiersza polecenia w pliku Web.config po stronie serwera zbiór [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikacji. Aby tego uniknąć, należy zmodyfikować plik Machine.config, aby uniemożliwić użytkownikom kompilowanie na serwerze.  
  
 Jeśli ta opcja jest używana z `/errorreport:prompt`, `/errorreport:queue`, lub `/errorreport:send`, a aplikacja napotka błąd wewnętrzny kompilatora, informacje w `file` są wysyłane do firmy Microsoft Corporation. Informacje te pomogą zidentyfikować przyczynę błędu pracownicy firmy Microsoft i może zwiększyć kolejnej wersji programu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Domyślnie żadne informacje nie są wysyłane do firmy Microsoft. Jednak gdy aplikacja jest skompilować przy użyciu `/errorreport:queue`aplikacji zbiera jego raporty o błędach, które jest domyślnie włączone. Następnie gdy administrator komputera loguje, system raportowania błędów wyświetla okno podręczne, które umożliwia administratorowi przekazywać do firmy Microsoft raporty wszelkie błędy, że od czasu logowania.  
  
> [!NOTE]
>  `/bugreport` Opcja nie jest dostępne w środowisku programowania Visual Studio; będzie dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje `T2.vb` i umieszcza wszystkie informacje o raportowaniu błędów w pliku `Problem.txt`.  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [/ errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [trustLevel elementu dla securityPolicy (schemat ustawień programu ASP.NET)](http://msdn.microsoft.com/en-us/729ab04c-03da-4ee5-86b1-be9d08a09369)
