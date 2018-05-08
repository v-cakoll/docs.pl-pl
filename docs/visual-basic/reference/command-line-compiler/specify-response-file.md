---
title: '@ (Określ plik odpowiedzi) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ad4201dcc094364899984e13c85f2f43a6467ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-specify-response-file-visual-basic"></a>@ (Określ plik odpowiedzi) (Visual Basic)
Określa plik, który zawiera opcje kompilatora i skompilować plików kodu źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Argumenty  
 `response_file`  
 Wymagana. Plik, który zawiera listę opcji kompilatora lub plików kodu źródłowego do skompilowania. Nazwę pliku należy ująć w cudzysłów ("") zawiera spację.  
  
## <a name="remarks"></a>Uwagi  
 Kompilator przetwarza opcje kompilatora i określone w pliku odpowiedzi, tak jakby były one określone w wierszu polecenia plików kodu źródłowego.  
  
 Aby określić więcej niż jeden plik odpowiedzi w kompilacji, należy określić wiele opcji pliku odpowiedzi, takie jak.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 W odpowiedzi na plik, wiele opcji kompilatora i plików kodu źródłowego może występować w jednym wierszu. Specyfikacja opcji kompilatora pojedyncza musi znajdować się w jednym wierszu (nie może obejmować wiele wierszy). Pliki odpowiedzi mogą mieć komentarze, które zaczynają się od `#` symbolu.  
  
 Możesz łączyć opcje określone w wierszu polecenia z opcjami w co najmniej jeden plik odpowiedzi. Kompilator przetwarza opcji polecenia, po ich napotkaniu. W związku z tym argumenty wiersza polecenia można zastąpić opcje wymienione wcześniej w plikach odpowiedzi. Z drugiej strony Opcje w pliku odpowiedzi musi zostać zastąpiona opcje wymienione wcześniej w wierszu polecenia lub w innych plików odpowiedzi.  
  
 Visual Basic zapewnia pliku Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe. Pliku Vbc.rsp znajduje się domyślnie, chyba że `-noconfig` jest używana opcja. Aby uzyskać więcej informacji, zobacz [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  `@` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Następujące wiersze są z przykładowy plik odpowiedzi.  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `@` opcji przy użyciu pliku odpowiedzi o nazwie `File1.rsp`.  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
