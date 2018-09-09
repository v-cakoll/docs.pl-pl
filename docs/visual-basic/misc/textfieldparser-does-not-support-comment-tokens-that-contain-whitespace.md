---
title: TextFieldParser nie obsługuje tokenami komentarzy, które zawierają odstęp
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: a8931d67cd728cf98bc4d83044c65fad6642b021
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252808"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a><span data-ttu-id="81917-102">TextFieldParser nie obsługuje tokenami komentarzy, które zawierają odstęp</span><span class="sxs-lookup"><span data-stu-id="81917-102">TextFieldParser does not support comment tokens that contain white space</span></span>
<span data-ttu-id="81917-103">Podano tokenu komentarz, który zawiera biały znak.</span><span class="sxs-lookup"><span data-stu-id="81917-103">A comment token that contains white space has been supplied.</span></span> <span data-ttu-id="81917-104">`TextFieldParser` Nie obsługuje tokenami komentarzy, zawierające biały znak, chyba że biały występuje na początku tokenu.</span><span class="sxs-lookup"><span data-stu-id="81917-104">The `TextFieldParser` does not support comment tokens that contain white space unless the white space occurs at the beginning of the token.</span></span> <span data-ttu-id="81917-105">Biały znak pojawiają się na początku token jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="81917-105">White space occurring at the beginning of a token is ignored.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="81917-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="81917-106">To correct this error</span></span>  
  
-   <span data-ttu-id="81917-107">Należy podać token prawidłowy komentarz.</span><span class="sxs-lookup"><span data-stu-id="81917-107">Supply a correct comment token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81917-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81917-108">See also</span></span>

- [<span data-ttu-id="81917-109">Właściwość TextFieldParser.CommentTokens</span><span class="sxs-lookup"><span data-stu-id="81917-109">TextFieldParser.CommentTokens Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)  
- [<span data-ttu-id="81917-110">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="81917-110">Parsing Text Files with the TextFieldParser Object</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
- [<span data-ttu-id="81917-111">TextFieldParser, obiekt</span><span class="sxs-lookup"><span data-stu-id="81917-111">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
