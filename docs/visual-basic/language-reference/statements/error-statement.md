---
title: Error — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 668ffbc7b8db73a706c5771bb0734a77f8fc0206
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351234"
---
# <a name="error-statement"></a><span data-ttu-id="5b456-102">Error — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="5b456-102">Error Statement</span></span>
<span data-ttu-id="5b456-103">Symuluje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="5b456-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b456-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b456-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="5b456-105">Części</span><span class="sxs-lookup"><span data-stu-id="5b456-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="5b456-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5b456-106">Required.</span></span> <span data-ttu-id="5b456-107">Może być dowolnym prawidłowym numerem błędu.</span><span class="sxs-lookup"><span data-stu-id="5b456-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b456-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b456-108">Remarks</span></span>  
 <span data-ttu-id="5b456-109">Instrukcja `Error` jest obsługiwana w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="5b456-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="5b456-110">W nowym kodzie, szczególnie podczas tworzenia obiektów, użyj metody `Raise` `Err` obiektu do wygenerowania błędów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5b456-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="5b456-111">Jeśli `errornumber` jest zdefiniowany, instrukcja `Error` wywołuje procedurę obsługi błędów po przypisaniu właściwości obiektu `Err` do następujących wartości domyślnych:</span><span class="sxs-lookup"><span data-stu-id="5b456-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="5b456-112">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5b456-112">Property</span></span>|<span data-ttu-id="5b456-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="5b456-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="5b456-114">Wartość określona jako argument instrukcji `Error`.</span><span class="sxs-lookup"><span data-stu-id="5b456-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="5b456-115">Może być dowolnym prawidłowym numerem błędu.</span><span class="sxs-lookup"><span data-stu-id="5b456-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="5b456-116">Nazwa bieżącego projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5b456-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="5b456-117">Wyrażenie ciągu odpowiadające wartości zwracanej funkcji `Error` dla określonego `Number`, jeśli ten ciąg istnieje.</span><span class="sxs-lookup"><span data-stu-id="5b456-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="5b456-118">Jeśli ciąg nie istnieje, `Description` zawiera ciąg o zerowej długości ("").</span><span class="sxs-lookup"><span data-stu-id="5b456-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="5b456-119">W pełni kwalifikowany dysk, ścieżka i nazwa pliku odpowiedniego pliku Pomocy języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5b456-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="5b456-120">Odpowiedni Visual Basic identyfikator kontekstu pliku pomocy dla błędu odpowiadającego właściwości `Number`.</span><span class="sxs-lookup"><span data-stu-id="5b456-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="5b456-121">Zero.</span><span class="sxs-lookup"><span data-stu-id="5b456-121">Zero.</span></span>|  
  
 <span data-ttu-id="5b456-122">Jeśli nie istnieje procedura obsługi błędów lub jeśli żadna nie jest włączona, zostanie utworzony komunikat o błędzie z właściwościami obiektu `Err`.</span><span class="sxs-lookup"><span data-stu-id="5b456-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b456-123">Niektóre aplikacje hosta Visual Basic nie mogą tworzyć obiektów.</span><span class="sxs-lookup"><span data-stu-id="5b456-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="5b456-124">Informacje o tym, czy aplikacja hosta może tworzyć klasy i obiekty, znajdziesz w jej dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="5b456-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b456-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b456-125">Example</span></span>  
 <span data-ttu-id="5b456-126">Ten przykład używa instrukcji `Error` w celu wygenerowania błędu o numerze 11.</span><span class="sxs-lookup"><span data-stu-id="5b456-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="5b456-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b456-127">Requirements</span></span>  
 <span data-ttu-id="5b456-128">**Przestrzeń nazw:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="5b456-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="5b456-129">**Zestaw:** Biblioteka środowiska uruchomieniowego Visual Basic (w pliku Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="5b456-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b456-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b456-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="5b456-131">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5b456-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="5b456-132">Resume, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5b456-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="5b456-133">Komunikaty o błędach</span><span class="sxs-lookup"><span data-stu-id="5b456-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
