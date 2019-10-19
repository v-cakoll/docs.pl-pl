---
title: Error — instrukcja (Visual Basic)
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
ms.openlocfilehash: c7b2adfe7f6b6ff5e89598cb318a90c51595ff6f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583376"
---
# <a name="error-statement"></a><span data-ttu-id="f682e-102">Error — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="f682e-102">Error Statement</span></span>
<span data-ttu-id="f682e-103">Symuluje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="f682e-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f682e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f682e-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="f682e-105">Części</span><span class="sxs-lookup"><span data-stu-id="f682e-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="f682e-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f682e-106">Required.</span></span> <span data-ttu-id="f682e-107">Może być dowolnym prawidłowym numerem błędu.</span><span class="sxs-lookup"><span data-stu-id="f682e-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f682e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f682e-108">Remarks</span></span>  
 <span data-ttu-id="f682e-109">Instrukcja `Error` jest obsługiwana w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="f682e-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="f682e-110">W nowym kodzie, szczególnie podczas tworzenia obiektów, użyj metody `Raise` `Err` obiektu do wygenerowania błędów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f682e-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="f682e-111">Jeśli `errornumber` jest zdefiniowany, instrukcja `Error` wywołuje procedurę obsługi błędów po przypisaniu właściwości obiektu `Err` do następujących wartości domyślnych:</span><span class="sxs-lookup"><span data-stu-id="f682e-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="f682e-112">Właściwość</span><span class="sxs-lookup"><span data-stu-id="f682e-112">Property</span></span>|<span data-ttu-id="f682e-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="f682e-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="f682e-114">Wartość określona jako argument instrukcji `Error`.</span><span class="sxs-lookup"><span data-stu-id="f682e-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="f682e-115">Może być dowolnym prawidłowym numerem błędu.</span><span class="sxs-lookup"><span data-stu-id="f682e-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="f682e-116">Nazwa bieżącego projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f682e-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="f682e-117">Wyrażenie ciągu odpowiadające wartości zwracanej funkcji `Error` dla określonego `Number`, jeśli ten ciąg istnieje.</span><span class="sxs-lookup"><span data-stu-id="f682e-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="f682e-118">Jeśli ciąg nie istnieje, `Description` zawiera ciąg o zerowej długości ("").</span><span class="sxs-lookup"><span data-stu-id="f682e-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="f682e-119">W pełni kwalifikowany dysk, ścieżka i nazwa pliku odpowiedniego pliku pomocy Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f682e-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="f682e-120">Odpowiedni Visual Basic identyfikator kontekstu pliku pomocy dla błędu odpowiadającego właściwości `Number`.</span><span class="sxs-lookup"><span data-stu-id="f682e-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="f682e-121">Zer.</span><span class="sxs-lookup"><span data-stu-id="f682e-121">Zero.</span></span>|  
  
 <span data-ttu-id="f682e-122">Jeśli nie istnieje procedura obsługi błędów lub jeśli żadna nie jest włączona, zostanie utworzony komunikat o błędzie z właściwościami obiektu `Err`.</span><span class="sxs-lookup"><span data-stu-id="f682e-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f682e-123">Niektóre Visual Basic aplikacje hosta nie mogą tworzyć obiektów.</span><span class="sxs-lookup"><span data-stu-id="f682e-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="f682e-124">Zapoznaj się z dokumentacją aplikacji hosta, aby określić, czy można tworzyć klasy i obiekty.</span><span class="sxs-lookup"><span data-stu-id="f682e-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f682e-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f682e-125">Example</span></span>  
 <span data-ttu-id="f682e-126">Ten przykład używa instrukcji `Error` w celu wygenerowania błędu o numerze 11.</span><span class="sxs-lookup"><span data-stu-id="f682e-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="f682e-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f682e-127">Requirements</span></span>  
 <span data-ttu-id="f682e-128">**Przestrzeń nazw:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="f682e-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="f682e-129">**Zestaw:** Biblioteka środowiska uruchomieniowego Visual Basic (w pliku Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="f682e-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f682e-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f682e-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="f682e-131">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f682e-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="f682e-132">Resume, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f682e-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="f682e-133">Komunikaty o błędach</span><span class="sxs-lookup"><span data-stu-id="f682e-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
