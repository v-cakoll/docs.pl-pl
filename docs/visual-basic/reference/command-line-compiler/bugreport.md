---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 440e583b55765d680ee72f8574f929e335e10cdb
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590628"
---
# <a name="-bugreport"></a>-bugreport
Tworzy plik, który można użyć, gdy plik jest raport o usterce.  
  
## <a name="syntax"></a>Składnia  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`file`|Wymagana. Nazwa pliku, który będzie zawierał raport o usterce. Nazwę pliku należy ująć w znaki cudzysłowu (""), jeśli nazwa zawiera spację.|  
  
## <a name="remarks"></a>Uwagi  
 Poniższe informacje są dodawane do `file`:  
  
- Kopiowanie wszystkich plików kodu źródłowego w kompilacji.  
  
- Lista opcji kompilatora, używane w kompilacji.  
  
- Informacje o wersji dotyczące kompilatora, środowisko uruchomieniowe języka wspólnego i systemu operacyjnego.  
  
- Kompilator dane wyjściowe, jeśli istnieje.  
  
- Opis problemu, dla którego jest wyświetlany monit.  
  
- Opis sposobu Twoim zdaniem ten problem należy ustalić, dla którego jest wyświetlany monit.  
  
 Ponieważ kopiowanie wszystkich plików kodu źródłowego jest uwzględniony w `file`, może zajść potrzeba odtworzenia kodu (podejrzanych) wada najkrótszej program możliwe.  
  
> [!IMPORTANT]
>  `-bugreport` Opcja tworzy plik, który zawiera potencjalnie poufne informacje. Obejmuje to bieżący czas, wersja kompilatora, wersja programu .NET Framework, wersja systemu operacyjnego, nazwę użytkownika, argumenty wiersza polecenia, z którymi kompilator zostało uruchomione, każdy kod źródłowy i binarną formę dowolnego przywoływanego zestawu. Ta opcja jest możliwy za pośrednictwem opcji wiersza polecenia w pliku Web.config dla kompilacji po stronie serwera w aplikacji ASP.NET. Aby tego uniknąć, należy zmodyfikować plik Machine.config, aby uniemożliwić użytkownikom kompilacji na serwerze.  
  
 Jeśli ta opcja jest używana z `-errorreport:prompt`, `-errorreport:queue`, lub `-errorreport:send`, i aplikacji wystąpi błąd wewnętrzny kompilatora, informacje zawarte w `file` są wysyłane do firmy Microsoft Corporation. Te informacje pomagają inżynierów firmy Microsoft, Zidentyfikuj przyczynę błędu i może poprawić kolejnej wersji programu Visual Basic. Domyślnie żadne informacje nie są wysyłane do firmy Microsoft. Jednakże, gdy kompilujesz aplikację za pomocą `-errorreport:queue`, która jest domyślnie włączone, aplikacja zbiera raporty o błędach. Następnie kiedy loguje administratora komputera, systemu raportowania błędów wyświetli okno wyskakujące z umożliwiająca administratorowi przesłać do firmy Microsoft raporty o wszelkich błędach, które od czasu logowania.  
  
> [!NOTE]
>  `/bugreport` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilacji z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje `T2.vb` i umieszczenie wszystkich informacji usługi raportowania błędów w pliku `Problem.txt`.  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [trustLevel elementu dla securityPolicy (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
