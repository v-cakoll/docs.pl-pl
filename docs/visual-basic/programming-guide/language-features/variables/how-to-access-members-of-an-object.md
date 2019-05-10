---
title: 'Instrukcje: Dostęp do elementów członkowskich obiektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 46c5eb9bc79b3a408a5a4fc9f40fee7391937c58
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663600"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="e03ab-102">Instrukcje: Dostęp do elementów członkowskich obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e03ab-102">How to: Access Members of an Object (Visual Basic)</span></span>
<span data-ttu-id="e03ab-103">Jeśli masz zmienną obiektu, który odwołuje się do obiektu, często chcą pracować z członkami tego obiektu, takie jak metody, właściwości, pola i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e03ab-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="e03ab-104">Na przykład po utworzeniu nowego <xref:System.Windows.Forms.Form> obiektu, warto ustawić jej <xref:System.Windows.Forms.Control.Text%2A> właściwość lub wywołanie jego <xref:System.Windows.Forms.Control.Focus%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e03ab-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>  
  
## <a name="accessing-members"></a><span data-ttu-id="e03ab-105">Uzyskiwanie dostępu do elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="e03ab-105">Accessing Members</span></span>  
 <span data-ttu-id="e03ab-106">Uzyskujesz dostęp do członków obiektu za pomocą zmiennej, która odwołuje się do niego.</span><span class="sxs-lookup"><span data-stu-id="e03ab-106">You access an object's members through the variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="e03ab-107">Aby dostęp do elementów członkowskich obiektu</span><span class="sxs-lookup"><span data-stu-id="e03ab-107">To access members of an object</span></span>  
  
- <span data-ttu-id="e03ab-108">Użyj operatora dostępu do elementu członkowskiego (`.`) między nazwą zmiennej obiektu i nazwę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e03ab-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     <span data-ttu-id="e03ab-109">Jeśli element jest [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), nie trzeba zmiennej, aby uzyskać do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="e03ab-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>  
  
## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="e03ab-110">Uzyskiwanie dostępu do elementów członkowskich obiektu znany typ</span><span class="sxs-lookup"><span data-stu-id="e03ab-110">Accessing Members of an Object of Known Type</span></span>  
 <span data-ttu-id="e03ab-111">Jeśli znasz typ obiektu w czasie kompilacji, możesz użyć *wczesne powiązania* zmiennej, która odwołuje się do niego.</span><span class="sxs-lookup"><span data-stu-id="e03ab-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="e03ab-112">Aby dostęp do elementów członkowskich obiektu, dla którego typ znany w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="e03ab-112">To access members of an object for which you know the type at compile time</span></span>  
  
1. <span data-ttu-id="e03ab-113">Zadeklaruj zmienną obiektu typu obiektu, który chcesz przypisać do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e03ab-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     <span data-ttu-id="e03ab-114">Za pomocą `Option Strict On`, można przypisać tylko <xref:System.Windows.Forms.Form> obiektów (lub obiektów typu pochodnego od <xref:System.Windows.Forms.Form>) do `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="e03ab-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="e03ab-115">Jeśli zdefiniowano klasy lub struktury za pomocą rozszerzenia `CType` konwersji <xref:System.Windows.Forms.Form>, można także przypisać tej klasy lub struktury do `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="e03ab-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>  
  
2. <span data-ttu-id="e03ab-116">Użyj operatora dostępu do elementu członkowskiego (`.`) między nazwą zmiennej obiektu i nazwę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e03ab-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    extraForm.Show()  
    ```  
  
     <span data-ttu-id="e03ab-117">Dostęp do wszystkich metod i właściwości specyficzne dla <xref:System.Windows.Forms.Form> klasy, niezależnie od tego, co `Option Strict` to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="e03ab-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="e03ab-118">Uzyskiwanie dostępu do elementów członkowskich obiektu nieznanego typu</span><span class="sxs-lookup"><span data-stu-id="e03ab-118">Accessing Members of an Object of Unknown Type</span></span>  
 <span data-ttu-id="e03ab-119">Jeśli typ obiektu nie jest znany w czasie kompilacji, należy użyć *późnym wiązaniu* dla dowolnej zmiennej, która odwołuje się do niego.</span><span class="sxs-lookup"><span data-stu-id="e03ab-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="e03ab-120">Aby dostęp do elementów członkowskich obiektu, dla którego nie znasz typu w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="e03ab-120">To access members of an object for which you do not know the type at compile time</span></span>  
  
1. <span data-ttu-id="e03ab-121">Deklarowanie zmiennej obiektu będzie [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e03ab-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="e03ab-122">(Zadeklarowanie zmiennej jako `Object` jest taka sama jak deklarowania go jako <xref:System.Object?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="e03ab-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>  
  
    ```  
    Dim someControl As Object  
    ```  
  
     <span data-ttu-id="e03ab-123">Za pomocą `Option Strict On`, możesz uzyskać dostęp tylko do elementów członkowskich, które są zdefiniowane na <xref:System.Object> klasy.</span><span class="sxs-lookup"><span data-stu-id="e03ab-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>  
  
2. <span data-ttu-id="e03ab-124">Użyj operatora dostępu do elementu członkowskiego (`.`) między nazwą zmiennej obiektu i nazwę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e03ab-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    someControl.GetType()  
    ```  
  
     <span data-ttu-id="e03ab-125">Aby umożliwić dostęp do elementów członkowskich obiektu można przypisać do zmiennej obiektu, należy ustawić `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="e03ab-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="e03ab-126">Gdy to zrobisz, kompilator nie może zagwarantować, że dany element jest uwidaczniany przez obiekt, który można przypisać do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e03ab-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="e03ab-127">Jeśli obiekt nie ujawnia członka, nastąpi próba uzyskania dostępu, <xref:System.MemberAccessException> wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e03ab-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e03ab-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e03ab-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="e03ab-129">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="e03ab-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="e03ab-130">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="e03ab-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="e03ab-131">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="e03ab-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="e03ab-132">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e03ab-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
