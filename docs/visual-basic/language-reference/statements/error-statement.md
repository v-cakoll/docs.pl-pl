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
ms.openlocfilehash: 8ac7cee2f9959bc75df165d00d3a0a67e1dd9af0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837536"
---
# <a name="error-statement"></a><span data-ttu-id="1fb3e-102">Error — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="1fb3e-102">Error Statement</span></span>
<span data-ttu-id="1fb3e-103">Symuluje wystąpieniu błędu.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fb3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fb3e-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="1fb3e-105">Części</span><span class="sxs-lookup"><span data-stu-id="1fb3e-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="1fb3e-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-106">Required.</span></span> <span data-ttu-id="1fb3e-107">Może być dowolnym prawidłowym numerem błędu.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fb3e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1fb3e-108">Remarks</span></span>  
 <span data-ttu-id="1fb3e-109">Instrukcja `Error` jest obsługiwana dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="1fb3e-110">W nowym kodzie, szczególnie w przypadku tworzenia obiektów, użyj metody `Raise` obiektu `Err`, aby generować błędy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="1fb3e-111">Jeśli `errornumber` jest zdefiniowany, instrukcja `Error` wywołuje program obsługi błędów po tym, jak do właściwości obiektu `Err` zostaną przypisane następujące wartości domyślne:</span><span class="sxs-lookup"><span data-stu-id="1fb3e-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="1fb3e-112">Właściwość</span><span class="sxs-lookup"><span data-stu-id="1fb3e-112">Property</span></span>|<span data-ttu-id="1fb3e-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="1fb3e-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="1fb3e-114">|`Number`|Wartość określona jako argument `Error` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="1fb3e-115">Może być dowolnym prawidłowym numerem błędu.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="1fb3e-116">Nazwa bieżącego projektu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="1fb3e-117">Wyrażenie ciągu odpowiadające zwracanej wartości funkcji `Error` dla podanej wartości `Number`, jeśli taki ciąg istnieje.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="1fb3e-118">Jeśli ciąg nie istnieje, wartość `Description` zawiera ciąg znaków o zerowej długości ("").</span><span class="sxs-lookup"><span data-stu-id="1fb3e-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="1fb3e-119">W pełni kwalifikowany dysk, ścieżka i nazwa pliku odpowiedniego pliku Pomocy języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="1fb3e-120">Odpowiedni identyfikator kontekstu pomocy języka Visual Basic dla błędu odpowiadającego właściwości `Number`.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="1fb3e-121">Zero.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-121">Zero.</span></span>|  
  
 <span data-ttu-id="1fb3e-122">Jeśli nie istnieje program do obsługi błędów lub jeśli żaden nie jest włączony, zostaje utworzony i wyświetlony komunikat o błędzie zawierający informacje z właściwości obiektu `Err`.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fb3e-123">Niektóre aplikacje hosta Visual Basic nie mogą tworzyć obiektów.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="1fb3e-124">Informacje o tym, czy aplikacja hosta może tworzyć klasy i obiekty, znajdziesz w jej dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fb3e-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="1fb3e-125">Example</span></span>  
 <span data-ttu-id="1fb3e-126">W tym przykładzie instrukcja `Error` została użyta do wygenerowania błędu numer 11.</span><span class="sxs-lookup"><span data-stu-id="1fb3e-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="1fb3e-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1fb3e-127">Requirements</span></span>  
 <span data-ttu-id="1fb3e-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="1fb3e-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="1fb3e-129">**Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="1fb3e-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb3e-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fb3e-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="1fb3e-131">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1fb3e-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="1fb3e-132">Resume, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1fb3e-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="1fb3e-133">Komunikaty o błędach</span><span class="sxs-lookup"><span data-stu-id="1fb3e-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
