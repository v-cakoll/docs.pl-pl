---
title: Właściwości zaimplementowane automatycznie (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: bc83163a024bd50d3e256b4eb49861669f8c02c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656334"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="78b0e-102">Właściwości zaimplementowane automatycznie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78b0e-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="78b0e-103">*Właściwości zaimplementowane automatycznie* można szybko określić właściwość klasy bez konieczności pisania kodu do `Get` i `Set` właściwości.</span><span class="sxs-lookup"><span data-stu-id="78b0e-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="78b0e-104">Podczas pisania kodu dla właściwości zaimplementowane automatycznie kompilator Visual Basic automatycznie tworzy pole prywatne do przechowywania zmiennej właściwość oprócz tworzenia skojarzony `Get` i `Set` procedur.</span><span class="sxs-lookup"><span data-stu-id="78b0e-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="78b0e-105">Właściwości zaimplementowane automatycznie właściwości, łącznie z wartości domyślnej, mogą być deklarowane w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="78b0e-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="78b0e-106">W poniższym przykładzie przedstawiono trzy deklaracje właściwości.</span><span class="sxs-lookup"><span data-stu-id="78b0e-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](./codesnippet/VisualBasic/auto-implemented-properties_1.vb)]  
  
 <span data-ttu-id="78b0e-107">Właściwości zaimplementowane automatycznie odpowiada właściwości, dla których wartość właściwości jest przechowywana w pole prywatne.</span><span class="sxs-lookup"><span data-stu-id="78b0e-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="78b0e-108">Poniższy przykład kodu pokazuje właściwości zaimplementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="78b0e-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](./codesnippet/VisualBasic/auto-implemented-properties_2.vb)]  
  
 <span data-ttu-id="78b0e-109">Poniższy przykład kodu zawiera kod odpowiednik w poprzednim przykładzie automatycznie implementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="78b0e-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](./codesnippet/VisualBasic/auto-implemented-properties_3.vb)]  
  
 <span data-ttu-id="78b0e-110">Poniższy kod Pokaż Implementowanie właściwości tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="78b0e-110">The following code show implementing readonly properties:</span></span>  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="78b0e-111">Jak pokazano w przykładzie można przypisać do właściwości, za pomocą wyrażeń inicjowania lub można przypisać do właściwości w Konstruktorze typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="78b0e-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="78b0e-112">W dowolnym momencie można przypisać do pola zapasowy właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="78b0e-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="78b0e-113">Pola zapasowego</span><span class="sxs-lookup"><span data-stu-id="78b0e-113">Backing Field</span></span>  
 <span data-ttu-id="78b0e-114">Właściwości zaimplementowane automatycznie w deklaracji, Visual Basic automatycznie tworzy ukryte pole prywatnej o nazwie *pole zapasowe* zawiera wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="78b0e-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="78b0e-115">Nazwa pola zapasowego jest nazwa właściwości zaimplementowane automatycznie poprzedzone znaku podkreślenia (_).</span><span class="sxs-lookup"><span data-stu-id="78b0e-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="78b0e-116">Na przykład, jeśli zadeklarować automatycznie implementowana właściwość o nazwie `ID`, nosi nazwę pola zapasowego `_ID`.</span><span class="sxs-lookup"><span data-stu-id="78b0e-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="78b0e-117">Jeśli dołączysz element członkowski klasy o nazwie `_ID`, tworzy konflikt nazw i Visual Basic zgłasza błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="78b0e-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="78b0e-118">Pole zapasowe ma również następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="78b0e-118">The backing field also has the following characteristics:</span></span>  
  
-   <span data-ttu-id="78b0e-119">Modyfikator dostępu do pola zapasowego jest zawsze `Private`nawet wtedy, gdy samej właściwości ma poziom dostępu do innego, takich jak `Public`.</span><span class="sxs-lookup"><span data-stu-id="78b0e-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
-   <span data-ttu-id="78b0e-120">Jeśli właściwość jest oznaczona jako `Shared`, pole zapasowe również jest udostępnione.</span><span class="sxs-lookup"><span data-stu-id="78b0e-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
-   <span data-ttu-id="78b0e-121">Pole zapasowe nie dotyczą atrybutów określonych dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="78b0e-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
-   <span data-ttu-id="78b0e-122">Pole zapasowe są dostępne z kodu w klasie i debugowania narzędzi, takich jak okna czujki.</span><span class="sxs-lookup"><span data-stu-id="78b0e-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="78b0e-123">Pole zapasowe nie są wyświetlane na liście uzupełniania IntelliSense programu word.</span><span class="sxs-lookup"><span data-stu-id="78b0e-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="78b0e-124">Inicjowanie właściwości zaimplementowane automatycznie</span><span class="sxs-lookup"><span data-stu-id="78b0e-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="78b0e-125">Dowolne wyrażenie, który może służyć do zainicjowania pola jest prawidłowa dla automatycznie implementowanej właściwości inicjowania.</span><span class="sxs-lookup"><span data-stu-id="78b0e-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="78b0e-126">Podczas inicjowania właściwości zaimplementowane automatycznie wyrażenie jest obliczane i przekazane do `Set` procedury dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="78b0e-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="78b0e-127">W poniższych przykładach kodu pokazano niektóre automatycznie implementowane właściwości, które obejmują wartości początkowe.</span><span class="sxs-lookup"><span data-stu-id="78b0e-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](./codesnippet/VisualBasic/auto-implemented-properties_4.vb)]  
  
 <span data-ttu-id="78b0e-128">Nie można zainicjować automatycznie implementowana właściwość, która jest elementem członkowskim `Interface`, lub oznaczona `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="78b0e-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="78b0e-129">Gdy zadeklarować właściwości zaimplementowane automatycznie jako element członkowski `Structure`, automatycznie implementowane właściwości można zainicjować tylko, jeśli jest oznaczony jako `Shared`.</span><span class="sxs-lookup"><span data-stu-id="78b0e-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="78b0e-130">Przy deklarowaniu automatycznie implementowanej właściwości w postaci tablicy nie można określić granice tablicy jawnego.</span><span class="sxs-lookup"><span data-stu-id="78b0e-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="78b0e-131">Jednak można podać wartość za pomocą inicjatora tablicy, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="78b0e-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](./codesnippet/VisualBasic/auto-implemented-properties_5.vb)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="78b0e-132">Definicje właściwości, które wymagają standardowej składni</span><span class="sxs-lookup"><span data-stu-id="78b0e-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="78b0e-133">Właściwości zaimplementowane automatycznie wygodne i obsługuje wiele scenariuszy programowania.</span><span class="sxs-lookup"><span data-stu-id="78b0e-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="78b0e-134">Istnieją jednak sytuacji, w których nie można używać właściwości zaimplementowane automatycznie i zamiast tego należy użyć standard, lub *rozwinięty*, składni właściwości.</span><span class="sxs-lookup"><span data-stu-id="78b0e-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="78b0e-135">Należy użyć składni definicji właściwości rozszerzonej, jeśli chcesz wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="78b0e-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
-   <span data-ttu-id="78b0e-136">Dodaj kod, aby `Get` lub `Set` procedury właściwości, takie jak kod do sprawdzania poprawności wartości przychodzących w `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="78b0e-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="78b0e-137">Na przykład można sprawdzić, czy ciąg reprezentujący numer telefonu zawiera wymaganą liczbę cyfr przed ustawieniem wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="78b0e-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
-   <span data-ttu-id="78b0e-138">Określ inną ułatwień dostępu dla `Get` i `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="78b0e-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="78b0e-139">Na przykład można wprowadzić `Set` procedury `Private` i `Get` procedury `Public`.</span><span class="sxs-lookup"><span data-stu-id="78b0e-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
-   <span data-ttu-id="78b0e-140">Utworzenie właściwości, które są `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="78b0e-140">Create properties that are `WriteOnly`.</span></span>  
  
-   <span data-ttu-id="78b0e-141">Użyj właściwości parametrycznego (w tym `Default` właściwości).</span><span class="sxs-lookup"><span data-stu-id="78b0e-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="78b0e-142">Musisz zadeklarować rozszerzonych właściwości w celu określenia parametru dla właściwości lub wymagają podania dodatkowych parametrów dla `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="78b0e-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
-   <span data-ttu-id="78b0e-143">Umieść atrybut na pole zapasowe lub zmień poziom dostępu pola zapasowego.</span><span class="sxs-lookup"><span data-stu-id="78b0e-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
-   <span data-ttu-id="78b0e-144">Podaj komentarze XML dla pola zapasowego.</span><span class="sxs-lookup"><span data-stu-id="78b0e-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="78b0e-145">Rozszerzanie właściwości zaimplementowane automatycznie</span><span class="sxs-lookup"><span data-stu-id="78b0e-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="78b0e-146">Jeśli trzeba przekonwertować automatycznie implementowanej właściwości rozszerzonych właściwości, który zawiera `Get` lub `Set` procedury edytora kodu języka Visual Basic może automatycznie generować `Get` i `Set` procedury i `End Property`instrukcji dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="78b0e-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="78b0e-147">Kod jest generowany, gdy kursor zostanie umieszczony na pusty wiersz poniżej `Property` instrukcji, a typ `G` (dla `Get`) lub `S` (dla `Set`) i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="78b0e-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="78b0e-148">Edytor kodu języka Visual Basic automatycznie generuje `Get` lub `Set` procedury dla właściwości tylko do odczytu i tylko do zapisu, po naciśnięciu klawisza ENTER na końcu `Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="78b0e-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b0e-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78b0e-149">See Also</span></span>  
 [<span data-ttu-id="78b0e-150">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="78b0e-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="78b0e-151">Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="78b0e-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="78b0e-152">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="78b0e-152">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="78b0e-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="78b0e-153">ReadOnly</span></span>](../../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="78b0e-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="78b0e-154">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="78b0e-155">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="78b0e-155">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
