---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: 5471f0783eee5e2c14cf0f140094d5c292a73756
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663261"
---
# <a name="-errorreport"></a><span data-ttu-id="d5c86-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="d5c86-102">-errorreport</span></span>

<span data-ttu-id="d5c86-103">Określa, jak kompilator języka Visual Basic powinno zgłosić wewnętrzne błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d5c86-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="d5c86-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5c86-104">Syntax</span></span>

```
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="d5c86-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5c86-105">Remarks</span></span>

<span data-ttu-id="d5c86-106">Ta opcja zapewnia wygodny sposób, aby zgłosić błąd wewnętrzny kompilatora Visual Basic (ICE) do zespołu języka Visual Basic w firmie Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d5c86-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="d5c86-107">Domyślnie kompilator wysyła żadnych informacji do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d5c86-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="d5c86-108">Jednak jeśli wystąpi błąd wewnętrzny kompilatora, ta opcja umożliwia raportowanie błędów firmie Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d5c86-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="d5c86-109">Te informacje pomagają inżynierów firmy Microsoft, zidentyfikować przyczynę i może poprawić kolejnej wersji programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d5c86-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="d5c86-110">Zdolność użytkownika do wysyłania raportów zależy od uprawnienia zasad komputera i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d5c86-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="d5c86-111">W poniższej tabeli przedstawiono efekt `-errorreport` opcji.</span><span class="sxs-lookup"><span data-stu-id="d5c86-111">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="d5c86-112">Opcja</span><span class="sxs-lookup"><span data-stu-id="d5c86-112">Option</span></span>|<span data-ttu-id="d5c86-113">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="d5c86-113">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="d5c86-114">Jeśli wystąpi błąd wewnętrzny kompilatora, okno dialogowe funkcjonuje tak, aby wyświetlić dokładnych danych zebranych przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="d5c86-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="d5c86-115">Można określić, czy ma żadnych poufnych informacji w raporcie o błędach i decyzji od tego, czy wysyłać je do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d5c86-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="d5c86-116">Jeśli zdecydujesz się wysłać go i zezwalają na to ustawienia zasad komputera i użytkownika, kompilator wysyła dane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d5c86-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="d5c86-117">Kolejkuje raport o błędach.</span><span class="sxs-lookup"><span data-stu-id="d5c86-117">Queues the error report.</span></span> <span data-ttu-id="d5c86-118">Po zalogowaniu się przy użyciu uprawnień administratora, możesz zgłaszać błędów od czasu ostatniego zostały zarejestrowane w (użytkownik nie jest monitowany o wysłanie raportu błędów więcej niż raz na trzy dni).</span><span class="sxs-lookup"><span data-stu-id="d5c86-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="d5c86-119">Jest to domyślne zachowanie podczas `-errorreport` opcja nie jest określona.</span><span class="sxs-lookup"><span data-stu-id="d5c86-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="d5c86-120">Jeśli wystąpi błąd wewnętrzny kompilatora i zezwalają na to ustawienia zasad komputera i użytkownika, kompilator wysyła dane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d5c86-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="d5c86-121">Opcja `-errorreport:send` próbuje automatycznie wysyłać informacje o błędach do firmy Microsoft, jeśli raportowania został włączony przez [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) ustawienia systemu.</span><span class="sxs-lookup"><span data-stu-id="d5c86-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="d5c86-122">Jeśli wystąpi błąd wewnętrzny kompilatora, go będzie nie być zbierane lub wysyłane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d5c86-122">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="d5c86-123">Kompilator wysyła dane, która zawiera stos w momencie wystąpienia błędu, który zwykle zawiera niektóre kody źródłowe.</span><span class="sxs-lookup"><span data-stu-id="d5c86-123">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="d5c86-124">Jeśli `-errorreport` jest używana z [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opcji, a następnie wysłaniu całego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d5c86-124">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="d5c86-125">Ta opcja jest optymalna dla [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opcji, ponieważ zezwala ona na inżynierów firmy Microsoft, aby łatwo odtworzyć błąd.</span><span class="sxs-lookup"><span data-stu-id="d5c86-125">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="d5c86-126">`-errorreport` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d5c86-126">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="d5c86-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5c86-127">Example</span></span>

<span data-ttu-id="d5c86-128">Poniższy kod próbuje skompilować `T2.vb`, i gdy kompilator napotka błąd wewnętrzny kompilatora, jednak monituje o wysłanie raportu o błędach do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d5c86-128">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="d5c86-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5c86-129">See also</span></span>

- [<span data-ttu-id="d5c86-130">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5c86-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d5c86-131">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d5c86-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="d5c86-132">-bugreport</span><span class="sxs-lookup"><span data-stu-id="d5c86-132">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
