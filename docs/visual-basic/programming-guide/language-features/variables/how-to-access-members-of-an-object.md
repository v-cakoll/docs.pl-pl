---
title: 'Instrukcje: Dostęp do elementów członkowskich obiektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 882046b829ade2da7c10b3db4c0d6c9ca9f3d579
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630834"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="a9da1-102">Instrukcje: Dostęp do elementów członkowskich obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9da1-102">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="a9da1-103">Gdy masz zmienną obiektu, która odwołuje się do obiektu, często chcesz współpracować z elementami członkowskimi tego obiektu, takimi jak metody, właściwości, pola i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a9da1-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="a9da1-104">Na przykład po utworzeniu nowego <xref:System.Windows.Forms.Form> obiektu można ustawić jego <xref:System.Windows.Forms.Control.Text%2A> właściwość lub wywołać <xref:System.Windows.Forms.Control.Focus%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="a9da1-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="a9da1-105">Dostęp do członków</span><span class="sxs-lookup"><span data-stu-id="a9da1-105">Accessing Members</span></span>

<span data-ttu-id="a9da1-106">Dostęp do elementów członkowskich obiektu można uzyskać za pomocą zmiennej, która odwołuje się do niej.</span><span class="sxs-lookup"><span data-stu-id="a9da1-106">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="a9da1-107">Aby uzyskać dostęp do elementów członkowskich obiektu</span><span class="sxs-lookup"><span data-stu-id="a9da1-107">To access members of an object</span></span>

- <span data-ttu-id="a9da1-108">Użyj operatora dostępu do elementów członkowskich (`.`) między nazwą zmiennej obiektu a nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="a9da1-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="a9da1-109">Jeśli element członkowski jest [współużytkowany](../../../../visual-basic/language-reference/modifiers/shared.md), nie potrzebujesz zmiennej, aby uzyskać do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="a9da1-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="a9da1-110">Uzyskiwanie dostępu do elementów członkowskich obiektu znanego typu</span><span class="sxs-lookup"><span data-stu-id="a9da1-110">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="a9da1-111">Jeśli znasz typ obiektu w czasie kompilacji, możesz użyć *wczesnego powiązania* dla zmiennej, która odwołuje się do niej.</span><span class="sxs-lookup"><span data-stu-id="a9da1-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="a9da1-112">Aby uzyskać dostęp do elementów członkowskich obiektu, dla którego znasz typ w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="a9da1-112">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="a9da1-113">Zadeklaruj zmienną obiektu jako typ obiektu, który ma zostać przypisany do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a9da1-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="a9da1-114">Za `Option Strict On`pomocą można przypisywać tylko <xref:System.Windows.Forms.Form> obiekty (lub obiekty typu pochodnego od <xref:System.Windows.Forms.Form>) do `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="a9da1-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="a9da1-115">Jeśli zdefiniowano klasę lub strukturę z `CType` konwersją rozszerzającą do <xref:System.Windows.Forms.Form>, można także przypisać tę klasę lub strukturę do `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="a9da1-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="a9da1-116">Użyj operatora dostępu do elementów członkowskich (`.`) między nazwą zmiennej obiektu a nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="a9da1-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="a9da1-117">Można uzyskać dostęp do wszystkich metod i właściwości specyficznych dla <xref:System.Windows.Forms.Form> klasy, niezależnie od tego `Option Strict` , co to jest ustawienie.</span><span class="sxs-lookup"><span data-stu-id="a9da1-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="a9da1-118">Uzyskiwanie dostępu do elementów członkowskich obiektu nieznanego typu</span><span class="sxs-lookup"><span data-stu-id="a9da1-118">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="a9da1-119">Jeśli nie znasz typu obiektu w czasie kompilacji, musisz użyć *późnego wiązania* dla każdej zmiennej, która odwołuje się do niej.</span><span class="sxs-lookup"><span data-stu-id="a9da1-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="a9da1-120">Aby uzyskać dostęp do elementów członkowskich obiektu, dla którego nie znasz typu w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="a9da1-120">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="a9da1-121">Zadeklaruj zmienną obiektu jako [Typ danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="a9da1-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="a9da1-122">(Deklarując zmienną tak `Object` samo jak deklarującą ją jako <xref:System.Object?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="a9da1-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="a9da1-123">W `Option Strict On`programie można uzyskać dostęp tylko do elementów członkowskich, które są zdefiniowane <xref:System.Object> w klasie.</span><span class="sxs-lookup"><span data-stu-id="a9da1-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="a9da1-124">Użyj operatora dostępu do elementów członkowskich (`.`) między nazwą zmiennej obiektu a nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="a9da1-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="a9da1-125">Aby można było uzyskać dostęp do elementów członkowskich dowolnego obiektu, który jest przypisany do zmiennej obiektu, należy ustawić `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="a9da1-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="a9da1-126">Gdy to zrobisz, kompilator nie może zagwarantować, że dany element członkowski jest uwidoczniony przez obiekt przypisany do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a9da1-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="a9da1-127">Jeśli obiekt nie ujawnia elementu członkowskiego, do którego próbujesz uzyskać dostęp <xref:System.MemberAccessException> , wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a9da1-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9da1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9da1-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="a9da1-129">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="a9da1-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="a9da1-130">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="a9da1-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="a9da1-131">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="a9da1-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="a9da1-132">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a9da1-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
