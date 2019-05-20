---
title: Konstruktory statyczne - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 110d83caad0c588fa899a4129897784e9c74aab8
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881915"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="9776d-102">Konstruktory statyczne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="9776d-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="9776d-103">Statyczny Konstruktor jest wykorzystywany do inicjacji dowolne [statyczne](../../../csharp/language-reference/keywords/static.md) danych, lub do wykonania określonej akcji, która musi zostać wykonana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="9776d-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="9776d-104">Jest wywoływana automatycznie przed pierwsze wystąpienie jest tworzone lub żadnych statycznych składowych są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="9776d-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
  
 <span data-ttu-id="9776d-105">Konstruktory statyczne mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="9776d-105">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="9776d-106">Statyczny Konstruktor zająć modyfikatory dostępu lub nie mieć parametrów.</span><span class="sxs-lookup"><span data-stu-id="9776d-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
- <span data-ttu-id="9776d-107">Statyczny Konstruktor jest wywoływana automatycznie zainicjować [klasy](../../../csharp/language-reference/keywords/class.md) przed pierwsze wystąpienie jest tworzone lub żadnych statycznych składowych są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="9776d-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="9776d-108">Należy pamiętać, że typ statyczny Konstruktor jest wywoływana po wywołaniu metody statycznej przypisanej do zdarzenia lub delegata, a nie w przypadku, gdy jest ona przypisana.</span><span class="sxs-lookup"><span data-stu-id="9776d-108">Note that a type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span>
  
- <span data-ttu-id="9776d-109">Konstruktor statyczny nie może wywołać bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="9776d-109">A static constructor cannot be called directly.</span></span>  
  
- <span data-ttu-id="9776d-110">Użytkownik nie ma kontroli na gdy Konstruktor statyczny jest wykonywane w programie.</span><span class="sxs-lookup"><span data-stu-id="9776d-110">The user has no control on when the static constructor is executed in the program.</span></span>  
  
- <span data-ttu-id="9776d-111">Typowym zastosowaniem konstruktorów statycznych jest, gdy klasa korzysta z pliku dziennika i konstruktora jest używany do zapisywania wpisów w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="9776d-111">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
- <span data-ttu-id="9776d-112">Konstruktory statyczne są także przydatne przy tworzeniu klas otoki dla niezarządzanego kodu podczas można wywołać konstruktora `LoadLibrary` metody.</span><span class="sxs-lookup"><span data-stu-id="9776d-112">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
- <span data-ttu-id="9776d-113">Jeśli statyczny Konstruktor zgłasza wyjątek, środowisko wykonawcze nie wywoła go drugi raz, a typ pozostanie niezainicjowanej okres istnienia domeny aplikacji, w którym jest uruchomiony program.</span><span class="sxs-lookup"><span data-stu-id="9776d-113">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9776d-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="9776d-114">Example</span></span>  
 <span data-ttu-id="9776d-115">W tym przykładzie klasa `Bus` ma Konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="9776d-115">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="9776d-116">Po pierwsze wystąpienie `Bus` zostanie utworzony (`bus1`), statyczny Konstruktor jest wywoływane w celu zainicjowania klasy.</span><span class="sxs-lookup"><span data-stu-id="9776d-116">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="9776d-117">Przykładowe dane wyjściowe weryfikuje, że Konstruktor statyczny działa tylko jeden raz, nawet jeśli dwa wystąpienia `Bus` są tworzone, to jest uruchamiane przed uruchomieniem konstruktora wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9776d-117">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]  
  
## <a name="see-also"></a><span data-ttu-id="9776d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9776d-118">See also</span></span>

- [<span data-ttu-id="9776d-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9776d-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9776d-120">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="9776d-120">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="9776d-121">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="9776d-121">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="9776d-122">Klasy statyczne i statyczne elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="9776d-122">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="9776d-123">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="9776d-123">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
