---
title: 'Porady: dostęp do elementów członkowskich obiektu'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: d44b538e8413eb1412e937375e9bca77600a29b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348668"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="d86aa-102">Porady: dostęp do elementów członkowskich obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d86aa-102">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="d86aa-103">Gdy masz zmienną obiektu, która odwołuje się do obiektu, często chcesz współpracować z elementami członkowskimi tego obiektu, takimi jak metody, właściwości, pola i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d86aa-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="d86aa-104">Na przykład po utworzeniu nowego obiektu <xref:System.Windows.Forms.Form> można ustawić jego właściwość <xref:System.Windows.Forms.Control.Text%2A> lub wywołać metodę <xref:System.Windows.Forms.Control.Focus%2A>.</span><span class="sxs-lookup"><span data-stu-id="d86aa-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="d86aa-105">Dostęp do członków</span><span class="sxs-lookup"><span data-stu-id="d86aa-105">Accessing Members</span></span>

<span data-ttu-id="d86aa-106">Dostęp do elementów członkowskich obiektu można uzyskać za pomocą zmiennej, która odwołuje się do niej.</span><span class="sxs-lookup"><span data-stu-id="d86aa-106">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="d86aa-107">Aby uzyskać dostęp do elementów członkowskich obiektu</span><span class="sxs-lookup"><span data-stu-id="d86aa-107">To access members of an object</span></span>

- <span data-ttu-id="d86aa-108">Użyj operatora dostępu do elementów członkowskich (`.`) między nazwą zmiennej obiektu a nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d86aa-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="d86aa-109">Jeśli element członkowski jest [współużytkowany](../../../../visual-basic/language-reference/modifiers/shared.md), nie potrzebujesz zmiennej, aby uzyskać do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="d86aa-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="d86aa-110">Uzyskiwanie dostępu do elementów członkowskich obiektu znanego typu</span><span class="sxs-lookup"><span data-stu-id="d86aa-110">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="d86aa-111">Jeśli znasz typ obiektu w czasie kompilacji, możesz użyć *wczesnego powiązania* dla zmiennej, która odwołuje się do niej.</span><span class="sxs-lookup"><span data-stu-id="d86aa-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="d86aa-112">Aby uzyskać dostęp do elementów członkowskich obiektu, dla którego znasz typ w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="d86aa-112">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="d86aa-113">Zadeklaruj zmienną obiektu jako typ obiektu, który ma zostać przypisany do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d86aa-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="d86aa-114">Za pomocą `Option Strict On`można przypisywać <xref:System.Windows.Forms.Form> obiektów (lub obiektów typu pochodzącego od <xref:System.Windows.Forms.Form>) do `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="d86aa-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="d86aa-115">Jeśli zdefiniowano klasę lub strukturę z rozszerzającą `CType` konwersji na <xref:System.Windows.Forms.Form>, można także przypisać tę klasę lub strukturę do `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="d86aa-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="d86aa-116">Użyj operatora dostępu do elementów członkowskich (`.`) między nazwą zmiennej obiektu a nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d86aa-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="d86aa-117">Można uzyskać dostęp do wszystkich metod i właściwości specyficznych dla klasy <xref:System.Windows.Forms.Form> niezależnie od tego, co ustawienie `Option Strict` ma wartość.</span><span class="sxs-lookup"><span data-stu-id="d86aa-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="d86aa-118">Uzyskiwanie dostępu do elementów członkowskich obiektu nieznanego typu</span><span class="sxs-lookup"><span data-stu-id="d86aa-118">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="d86aa-119">Jeśli nie znasz typu obiektu w czasie kompilacji, musisz użyć *późnego wiązania* dla każdej zmiennej, która odwołuje się do niej.</span><span class="sxs-lookup"><span data-stu-id="d86aa-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="d86aa-120">Aby uzyskać dostęp do elementów członkowskich obiektu, dla którego nie znasz typu w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="d86aa-120">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="d86aa-121">Zadeklaruj zmienną obiektu jako [Typ danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="d86aa-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="d86aa-122">(Deklarując zmienną jako `Object` jest taka sama jak deklarująca ją jako <xref:System.Object?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="d86aa-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="d86aa-123">Za pomocą `Option Strict On`można uzyskać dostęp tylko do elementów członkowskich, które są zdefiniowane w klasie <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="d86aa-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="d86aa-124">Użyj operatora dostępu do elementów członkowskich (`.`) między nazwą zmiennej obiektu a nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d86aa-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="d86aa-125">Aby można było uzyskać dostęp do elementów członkowskich dowolnego obiektu, który jest przypisany do zmiennej obiektu, należy ustawić `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="d86aa-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="d86aa-126">Gdy to zrobisz, kompilator nie może zagwarantować, że dany element członkowski jest uwidoczniony przez obiekt przypisany do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d86aa-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="d86aa-127">Jeśli obiekt nie ujawnia elementu członkowskiego, do którego próbujesz uzyskać dostęp, wystąpi wyjątek <xref:System.MemberAccessException>.</span><span class="sxs-lookup"><span data-stu-id="d86aa-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="d86aa-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d86aa-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="d86aa-129">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="d86aa-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="d86aa-130">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="d86aa-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="d86aa-131">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="d86aa-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="d86aa-132">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d86aa-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
