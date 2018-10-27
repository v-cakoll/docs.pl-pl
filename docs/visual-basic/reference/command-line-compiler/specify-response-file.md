---
title: '@ (Określ plik odpowiedzi) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 54a4cee0b779c0784eec169a15ab1594c56cede9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194686"
---
# <a name="-specify-response-file-visual-basic"></a>@ (Określ plik odpowiedzi) (Visual Basic)
Określa plik, który zawiera opcje kompilatora i pliki kodu źródłowego do kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Argumenty  
 `response_file`  
 Wymagana. Plik, który zawiera listę opcji kompilatora lub pliki kodu źródłowego do skompilowania. Nazwę pliku należy ująć w znaki cudzysłowu ("") zawiera spację.  
  
## <a name="remarks"></a>Uwagi  
 Kompilator przetwarza opcje kompilatora i pliki kodu źródłowego, określone w pliku odpowiedzi, tak, jakby były one określone w wierszu polecenia.  
  
 Aby określić więcej niż jeden plik odpowiedzi w kompilacji, należy określić wiele opcji pliku odpowiedzi, takie jak następujące.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 W odpowiedzi na plik, wiele opcji kompilatora i pliki kodu źródłowego może znajdować się w jednym wierszu. Specyfikacja pojedynczego opcję kompilatora musi znajdować się w jednym wierszu (nie może obejmować wiele wierszy). Pliki odpowiedzi mogą mieć komentarze, które zaczynają się od `#` symboli.  
  
 Można połączyć opcje określone w wierszu polecenia za pomocą opcji określonych w co najmniej jeden plik odpowiedzi. Po ich napotkaniu, kompilator przetwarza opcje polecenia. W związku z tym argumenty wiersza polecenia można zastąpić opcje wymienione wcześniej w plikach odpowiedzi. Z drugiej strony Opcje w pliku odpowiedzi zastępują opcje wymienione wcześniej w wierszu polecenia lub w innych plikach odpowiedzi.  
  
 Soubor Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe zapewnia Visual Basic. Soubor Vbc.rsp jest zawarte domyślnie, chyba że `-noconfig` jest używana opcja. Aby uzyskać więcej informacji, zobacz [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  `@` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Następujące wiersze pochodzą z przykładowego pliku odpowiedzi.  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób użycia `@` opcji z pliku odpowiedzi o nazwie `File1.rsp`.  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
