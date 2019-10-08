---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: c8e193a8cb4d4dbc7515c32139bad9dce8b48ed7
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005614"
---
# <a name="-errorreport"></a><span data-ttu-id="5a8bd-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="5a8bd-102">-errorreport</span></span>

<span data-ttu-id="5a8bd-103">Określa sposób, w jaki kompilator Visual Basic powinien raportować wewnętrzne błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="5a8bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a8bd-104">Syntax</span></span>

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="5a8bd-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a8bd-105">Remarks</span></span>

<span data-ttu-id="5a8bd-106">Ta opcja zapewnia wygodny sposób raportowania Visual Basic wewnętrznego błędu kompilatora (lodem) do zespołu Visual Basic w firmie Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="5a8bd-107">Domyślnie kompilator nie wysyła żadnych informacji do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="5a8bd-108">Jeśli jednak wystąpi błąd wewnętrzny kompilatora, ta opcja pozwala zgłosić błąd do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="5a8bd-109">Te informacje ułatwią inżynierom firmy Microsoft Identyfikowanie przyczyny i mogą pomóc w ulepszaniu kolejnej wersji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="5a8bd-110">Możliwość wysyłania raportów przez użytkownika zależy od uprawnień zasad komputera i użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="5a8bd-111">Poniższa tabela zawiera podsumowanie wpływu opcji `-errorreport`.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-111">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="5a8bd-112">Opcja</span><span class="sxs-lookup"><span data-stu-id="5a8bd-112">Option</span></span>|<span data-ttu-id="5a8bd-113">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="5a8bd-113">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="5a8bd-114">Jeśli wystąpi wewnętrzny błąd kompilatora, pojawi się okno dialogowe, które umożliwia wyświetlenie dokładnych danych zebranych przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="5a8bd-115">Można określić, czy w raporcie o błędach znajdują się informacje poufne i podjąć decyzję o tym, czy wysłać ją do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="5a8bd-116">Jeśli użytkownik zdecyduje się ją wysłać, a ustawienia zasad komputera i użytkownika zezwalają na to, kompilator wysyła dane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="5a8bd-117">Kolejkuje raport o błędach.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-117">Queues the error report.</span></span> <span data-ttu-id="5a8bd-118">Gdy logujesz się przy użyciu uprawnień administratora, możesz zgłosić błędy od momentu ostatniego logowania (nie będzie wyświetlany monit o wysłanie raportów dla błędów więcej niż raz na trzy dni).</span><span class="sxs-lookup"><span data-stu-id="5a8bd-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="5a8bd-119">Jest to zachowanie domyślne, gdy opcja `-errorreport` nie została określona.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="5a8bd-120">Jeśli wystąpi wewnętrzny błąd kompilatora, a ustawienia zasad komputera i użytkownika zezwalają na to, kompilator wysyła dane do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="5a8bd-121">Opcja `-errorreport:send` próbuje automatycznie wysłać informacje o błędzie do firmy Microsoft, jeśli raportowanie jest włączone przez ustawienia systemu [raportowanie błędów systemu Windows](/windows/desktop/wer/windows-error-reporting) .</span><span class="sxs-lookup"><span data-stu-id="5a8bd-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="5a8bd-122">W przypadku wystąpienia wewnętrznego błędu kompilatora nie będzie on zbierany ani wysyłany do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-122">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="5a8bd-123">Kompilator wysyła dane, które obejmują stos w momencie błędu, co zwykle zawiera kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-123">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="5a8bd-124">Jeśli `-errorreport` jest używany z opcją [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) , zostanie wysłany cały plik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-124">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="5a8bd-125">Ta opcja jest najlepiej używana z opcją [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) , ponieważ umożliwia inżynierom firmy Microsoft łatwiejsze odtwarzanie błędu.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-125">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="5a8bd-126">Opcja `-errorreport` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-126">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="5a8bd-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a8bd-127">Example</span></span>

<span data-ttu-id="5a8bd-128">Poniższy kod próbuje skompilować `T2.vb`, a jeśli kompilator napotyka wewnętrzny błąd kompilatora, zostanie wyświetlony komunikat z prośbą o wysłanie raportu o błędach do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5a8bd-128">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="5a8bd-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a8bd-129">See also</span></span>

- [<span data-ttu-id="5a8bd-130">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a8bd-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="5a8bd-131">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="5a8bd-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="5a8bd-132">-bugreport</span><span class="sxs-lookup"><span data-stu-id="5a8bd-132">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
