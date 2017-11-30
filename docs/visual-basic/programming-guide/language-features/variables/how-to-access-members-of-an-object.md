---
title: "Porady: dostęp do elementów członkowskich obiektu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 85fa4932b449bf7b9ecb3902fc17fd954ea8cfac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="01267-102">Porady: dostęp do elementów członkowskich obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01267-102">How to: Access Members of an Object (Visual Basic)</span></span>
<span data-ttu-id="01267-103">Jeśli masz zmiennej obiektu, który odwołuje się do obiektu często chcesz pracować z elementami członkowskimi tego obiektu, takie jak metod, właściwości, pól i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="01267-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="01267-104">Na przykład po utworzeniu nowego <xref:System.Windows.Forms.Form> obiektu, należy ustawić jej <xref:System.Windows.Forms.Control.Text%2A> właściwość lub wywołanie jego <xref:System.Windows.Forms.Control.Focus%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="01267-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>  
  
## <a name="accessing-members"></a><span data-ttu-id="01267-105">Uzyskiwanie dostępu do elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="01267-105">Accessing Members</span></span>  
 <span data-ttu-id="01267-106">Za pomocą zmiennej, która odwołuje się do niego dostęp do elementów członkowskich obiektu.</span><span class="sxs-lookup"><span data-stu-id="01267-106">You access an object's members through the variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="01267-107">Aby uzyskać dostępu do elementów członkowskich obiektu</span><span class="sxs-lookup"><span data-stu-id="01267-107">To access members of an object</span></span>  
  
-   <span data-ttu-id="01267-108">Użycie operatora dostępu do elementu członkowskiego (`.`) między nazwą zmiennej obiektu i nazwę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="01267-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     <span data-ttu-id="01267-109">Jeśli element członkowski jest [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), nie trzeba zmienną do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="01267-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>  
  
## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="01267-110">Uzyskiwanie dostępu do elementów członkowskich obiektu znanego typu</span><span class="sxs-lookup"><span data-stu-id="01267-110">Accessing Members of an Object of Known Type</span></span>  
 <span data-ttu-id="01267-111">Jeśli w czasie kompilacji jest znany typ obiektu, możesz użyć *wczesne wiązanie* zmiennej, która odwołuje się do niego.</span><span class="sxs-lookup"><span data-stu-id="01267-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="01267-112">Aby dostęp do elementów członkowskich obiektu, dla którego znany typ w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="01267-112">To access members of an object for which you know the type at compile time</span></span>  
  
1.  <span data-ttu-id="01267-113">Deklarowanie zmiennej obiektu typu obiektu, który chcesz przypisać do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="01267-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     <span data-ttu-id="01267-114">Z `Option Strict On`, można przypisać tylko <xref:System.Windows.Forms.Form> obiektów (lub obiektów typu pochodzącego od <xref:System.Windows.Forms.Form>) do `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="01267-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="01267-115">Jeśli zdefiniowano klasy lub struktury z rozszerzanie `CType` konwersji do <xref:System.Windows.Forms.Form>, można również przypisać tej klasy lub struktury do `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="01267-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>  
  
2.  <span data-ttu-id="01267-116">Użycie operatora dostępu do elementu członkowskiego (`.`) między nazwą zmiennej obiektu i nazwę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="01267-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    extraForm.Show()  
    ```  
  
     <span data-ttu-id="01267-117">Uzyskiwać dostęp do wszystkich metod i właściwości specyficzne dla <xref:System.Windows.Forms.Form> klasy, niezależnie od tego, co `Option Strict` to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="01267-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="01267-118">Uzyskiwanie dostępu do elementów członkowskich obiektu nieznanego typu.</span><span class="sxs-lookup"><span data-stu-id="01267-118">Accessing Members of an Object of Unknown Type</span></span>  
 <span data-ttu-id="01267-119">Jeśli nie znasz typu obiektu w czasie kompilacji, należy użyć *późne wiązanie* dla dowolnej zmiennej, która odwołuje się do niego.</span><span class="sxs-lookup"><span data-stu-id="01267-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="01267-120">Aby dostęp do elementów członkowskich obiektu, dla których nie wiadomo, typ w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="01267-120">To access members of an object for which you do not know the type at compile time</span></span>  
  
1.  <span data-ttu-id="01267-121">Deklarowanie zmiennej obiektu za [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="01267-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="01267-122">(Deklarowanie zmiennej jako `Object` jest taka sama jak deklarowanie go jako <xref:System.Object?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="01267-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>  
  
    ```  
    Dim someControl As Object  
    ```  
  
     <span data-ttu-id="01267-123">Z `Option Strict On`, można uzyskać dostęp tylko do elementów członkowskich, które są zdefiniowane na <xref:System.Object> klasy.</span><span class="sxs-lookup"><span data-stu-id="01267-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>  
  
2.  <span data-ttu-id="01267-124">Użycie operatora dostępu do elementu członkowskiego (`.`) między nazwą zmiennej obiektu i nazwę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="01267-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    someControl.GetType()  
    ```  
  
     <span data-ttu-id="01267-125">Aby można było uzyskać dostępu do elementów członkowskich obiektu przypisanie zmiennej obiektu, należy ustawić `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="01267-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="01267-126">Gdy to zrobisz, kompilator nie może zagwarantować, że dany element jest udostępniana przez obiekt, który można przypisać do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="01267-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="01267-127">Jeśli obiekt nie ujawnia członka próbie uzyskania dostępu, <xref:System.MemberAccessException> Wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="01267-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01267-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01267-128">See Also</span></span>  
 <xref:System.Object>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.MemberAccessException>  
 [<span data-ttu-id="01267-129">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="01267-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="01267-130">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="01267-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="01267-131">Object — typ danych</span><span class="sxs-lookup"><span data-stu-id="01267-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="01267-132">Option Strict — instrukcja</span><span class="sxs-lookup"><span data-stu-id="01267-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
