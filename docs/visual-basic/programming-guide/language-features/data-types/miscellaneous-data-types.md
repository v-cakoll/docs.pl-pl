---
title: "Różne typy danych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6bb86bb6d203aa4e6bdded27a4cb78a8155ddec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="754c2-102">Różne typy danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="754c2-102">Miscellaneous Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="754c2-103">udostępnia kilka typów danych, które nie są zorientowanych w kierunku cyfry lub znaki.</span><span class="sxs-lookup"><span data-stu-id="754c2-103"> supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="754c2-104">Zamiast tego mają do czynienia specjalne dane takie jak tak/nie wartości, wartości daty/godziny i adresy obiektu.</span><span class="sxs-lookup"><span data-stu-id="754c2-104">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="754c2-105">Dla Tabela zawierająca porównanie side-by-side [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] , zobacz [typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span><span class="sxs-lookup"><span data-stu-id="754c2-105">For a table showing a side-by-side comparison of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="754c2-106">Typ Boolean</span><span class="sxs-lookup"><span data-stu-id="754c2-106">Boolean Type</span></span>  
 <span data-ttu-id="754c2-107">[— Typ danych logicznych](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) jest wartość bez znaku, który jest interpretowany jako `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="754c2-107">The [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="754c2-108">Szerokość danych zależy od platformy implementującej.</span><span class="sxs-lookup"><span data-stu-id="754c2-108">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="754c2-109">Jeśli zmienna może zawierać tylko dwa wartości, takie jak PRAWDA/FAŁSZ tak/nie lub Włącz/Wyłącz, Zadeklaruj ją jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="754c2-109">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="754c2-110">Date — typ</span><span class="sxs-lookup"><span data-stu-id="754c2-110">Date Type</span></span>  
 <span data-ttu-id="754c2-111">[Date — typ danych](../../../../visual-basic/language-reference/data-types/date-data-type.md) jest wartością 64-bitowego, która przechowuje informacje zarówno datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="754c2-111">The [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="754c2-112">Jednostka reprezentuje 100 nanosekundach czas, który upłynął od początku (00:00:00) 1 stycznia 1 rok kalendarza gregoriańskiego.</span><span class="sxs-lookup"><span data-stu-id="754c2-112">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="754c2-113">Jeśli zmienna może zawierać wartości daty i godziny, Zadeklaruj ją jako `Date`.</span><span class="sxs-lookup"><span data-stu-id="754c2-113">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="754c2-114">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="754c2-114">Object Type</span></span>  
 <span data-ttu-id="754c2-115">[Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md) jest 32-bitowy adres, który wskazuje na wystąpienie obiektu w aplikacji lub w innej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="754c2-115">The [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="754c2-116">`Object` Zmiennej może odwoływać się do dowolnego obiektu aplikacja rozpoznaje lub danych dowolnego typu danych.</span><span class="sxs-lookup"><span data-stu-id="754c2-116">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="754c2-117">Dotyczy to zarówno *typów wartości*, takich jak `Integer`, `Boolean`i wystąpienia struktury i *typy referencyjne*, które są wystąpienia obiektów, takich jak utworzone na podstawie klasy `String`i <xref:System.Windows.Forms.Form>, a tablica wystąpień.</span><span class="sxs-lookup"><span data-stu-id="754c2-117">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="754c2-118">Jeśli zmienna przechowuje wskaźnik do wystąpienia klasy, która nie wiadomo, w czasie kompilacji lub dane różnych typów danych może wskazywać, Zadeklaruj ją jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="754c2-118">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="754c2-119">Zaletą `Object` — typ danych jest, że można użyć go do przechowywania danych dowolnego typu danych.</span><span class="sxs-lookup"><span data-stu-id="754c2-119">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="754c2-120">Wadą jest pociągnąć za sobą dodatkowe operacje zająć więcej czasu wykonywania i zwiększyć bezpieczeństwo aplikacji działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="754c2-120">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="754c2-121">Jeśli używasz `Object` ponieść zmiennej dla typów wartości, *boxing* i *rozpakowującej*.</span><span class="sxs-lookup"><span data-stu-id="754c2-121">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="754c2-122">Jeśli używasz dla typów odwołań ponosisz *późne wiązanie*.</span><span class="sxs-lookup"><span data-stu-id="754c2-122">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="754c2-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="754c2-123">See Also</span></span>  
 [<span data-ttu-id="754c2-124">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="754c2-124">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [<span data-ttu-id="754c2-125">Podstawowe typy danych</span><span class="sxs-lookup"><span data-stu-id="754c2-125">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="754c2-126">Numeryczne typy danych</span><span class="sxs-lookup"><span data-stu-id="754c2-126">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [<span data-ttu-id="754c2-127">Znakowe typy danych</span><span class="sxs-lookup"><span data-stu-id="754c2-127">Character Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [<span data-ttu-id="754c2-128">Rozwiązywanie problemów z typów danych</span><span class="sxs-lookup"><span data-stu-id="754c2-128">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="754c2-129">Wczesne i późne powiązania</span><span class="sxs-lookup"><span data-stu-id="754c2-129">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
