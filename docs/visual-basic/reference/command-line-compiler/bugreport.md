---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 829c19d2bce40a850d98f4973b1a4e4de31d8ce1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716816"
---
# <a name="-bugreport"></a>-bugreport
Tworzy plik, którego można użyć podczas tworzenia pliku raportu o usterce.  
  
## <a name="syntax"></a>Składnia  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`file`|Wymagany. Nazwa pliku, który będzie zawierać raport o błędach. Nazwa pliku powinna być ujęta w cudzysłów (""), jeśli nazwa zawiera spację.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące informacje są dodawane do `file`:  
  
- Kopia wszystkich plików kodu źródłowego w kompilacji.  
  
- Lista opcji kompilatora używanych w kompilacji.  
  
- Informacje o wersji dotyczące kompilatora, środowiska uruchomieniowego języka wspólnego i systemu operacyjnego.  
  
- Dane wyjściowe kompilatora, jeśli istnieją.  
  
- Opis problemu, dla którego zostanie wyświetlony monit.  
  
- Opis sposobu, w jaki sądzisz, że problem powinien zostać rozwiązany, dla którego zostanie wyświetlony monit.  
  
 Ze względu na to, że kopia wszystkich plików kodu źródłowego jest dołączona do `file`, warto odtworzyć defekt kodu (podejrzane) w najkrótszym możliwym programie.  
  
> [!IMPORTANT]
> Opcja `-bugreport` tworzy plik, który zawiera potencjalnie poufne informacje. Obejmuje to bieżący czas, wersję kompilatora, wersję .NET Framework, wersję systemu operacyjnego, nazwę użytkownika, argumenty wiersza polecenia, za pomocą których kompilator został uruchomiony, wszystkie kod źródłowy oraz binarną postać dowolnego przywoływanego zestawu. Dostęp do tej opcji można uzyskać, określając opcje wiersza polecenia w pliku Web. config po stronie serwera dla kompilacji aplikacji ASP.NET. Aby tego uniknąć, należy zmodyfikować plik Machine. config, aby nie zezwalać użytkownikom na kompilowanie na serwerze.  
  
 Jeśli ta opcja jest używana z `-errorreport:prompt`, `-errorreport:queue`lub `-errorreport:send`, a aplikacja napotka wewnętrzny błąd kompilatora, informacje w `file` są wysyłane do firmy Microsoft Corporation. Te informacje ułatwią inżynierom firmy Microsoft Identyfikowanie przyczyny błędu i mogą pomóc w ulepszaniu kolejnej wersji Visual Basic. Domyślnie żadne informacje nie są wysyłane do firmy Microsoft. Jednak podczas kompilowania aplikacji przy użyciu `-errorreport:queue`, która jest domyślnie włączona, aplikacja zbiera raporty o błędach. Po zalogowaniu się administratora komputera w systemie raportowanie błędów zostanie wyświetlone okno podręczne, które umożliwi administratorowi przekazanie do firmy Microsoft wszelkich raportów o błędach, które wystąpiły od momentu zalogowania.  
  
> [!NOTE]
> Opcja `-bugreport` nie jest dostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje `T2.vb` i umieszcza wszystkie informacje o raportowaniu błędów w `Problem.txt`pliku.  
  
```console  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Element trustLevel dla securityPolicy (ASP.NET Schema Settings)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
