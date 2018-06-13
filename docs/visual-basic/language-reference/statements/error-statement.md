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
ms.openlocfilehash: 3ecfe18392de15dc937d90565b49641415dd7e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603889"
---
# <a name="error-statement"></a><span data-ttu-id="13c28-102">Error — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="13c28-102">Error Statement</span></span>
<span data-ttu-id="13c28-103">Symuluje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="13c28-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c28-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13c28-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="13c28-105">Części</span><span class="sxs-lookup"><span data-stu-id="13c28-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="13c28-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="13c28-106">Required.</span></span> <span data-ttu-id="13c28-107">Może być dowolnym prawidłowym numerem błędu.</span><span class="sxs-lookup"><span data-stu-id="13c28-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13c28-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13c28-108">Remarks</span></span>  
 <span data-ttu-id="13c28-109">`Error` Instrukcja jest obsługiwana dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="13c28-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="13c28-110">Nowy kod, szczególnie w przypadku tworzenia obiektów, użyj `Err` obiektu `Raise` metodę, aby generować błędy czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="13c28-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="13c28-111">Jeśli `errornumber` jest zdefiniowany, `Error` instrukcji wywołuje program obsługi błędów po właściwości `Err` obiektu są przypisane następujące wartości domyślne:</span><span class="sxs-lookup"><span data-stu-id="13c28-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="13c28-112">Właściwość</span><span class="sxs-lookup"><span data-stu-id="13c28-112">Property</span></span>|<span data-ttu-id="13c28-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="13c28-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="13c28-114">Wartość określona jako argument `Error` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="13c28-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="13c28-115">Może być dowolnym prawidłowym numerem błędu.</span><span class="sxs-lookup"><span data-stu-id="13c28-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="13c28-116">Nazwa bieżącego projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13c28-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="13c28-117">Wyrażenie odpowiadające zwracanej wartości tekstowe `Error` funkcja dla określonego `Number`, jeśli istnieje ten ciąg.</span><span class="sxs-lookup"><span data-stu-id="13c28-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="13c28-118">Jeśli ciąg nie istnieje, `Description` zawiera ciąg o zerowej długości ("").</span><span class="sxs-lookup"><span data-stu-id="13c28-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="13c28-119">Dysk pełny, ścieżka i nazwa pliku odpowiedniego pliku Pomocy programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13c28-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="13c28-120">Odpowiednie pomocy programu Visual Basic identyfikator kontekstu błąd odpowiadający do pliku `Number` właściwości.</span><span class="sxs-lookup"><span data-stu-id="13c28-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="13c28-121">Zero.</span><span class="sxs-lookup"><span data-stu-id="13c28-121">Zero.</span></span>|  
  
 <span data-ttu-id="13c28-122">Jeśli istnieje bez obsługi błędu, lub jeśli brak jest włączona, komunikat o błędzie jest tworzone i wyświetlane z `Err` właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="13c28-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13c28-123">Niektóre aplikacje hosta Visual Basic nie można utworzyć obiektów.</span><span class="sxs-lookup"><span data-stu-id="13c28-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="13c28-124">Zapoznaj się dokumentacją aplikacji do określenia, czy można utworzyć w klas i obiektów.</span><span class="sxs-lookup"><span data-stu-id="13c28-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13c28-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="13c28-125">Example</span></span>  
 <span data-ttu-id="13c28-126">W tym przykładzie użyto `Error` instrukcję do wygenerowania 11. numer błędu.</span><span class="sxs-lookup"><span data-stu-id="13c28-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="13c28-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13c28-127">Requirements</span></span>  
 <span data-ttu-id="13c28-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="13c28-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="13c28-129">**Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="13c28-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c28-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13c28-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [<span data-ttu-id="13c28-131">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="13c28-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [<span data-ttu-id="13c28-132">Resume, instrukcja</span><span class="sxs-lookup"><span data-stu-id="13c28-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="13c28-133">Komunikaty o błędach</span><span class="sxs-lookup"><span data-stu-id="13c28-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
