---
title: Instrukcje dotyczące zapory
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: f1b576b4e413fa3bae70ef1eb8f8ed768e28e309
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295162"
---
# <a name="firewall-instructions"></a><span data-ttu-id="2ff4b-102">Instrukcje dotyczące zapory</span><span class="sxs-lookup"><span data-stu-id="2ff4b-102">Firewall Instructions</span></span>
<span data-ttu-id="2ff4b-103">Należy włączyć kilka portów i programów w zaporze, aby mógł działać przykładów Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2ff4b-103">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="2ff4b-104">Wiele przykładów komunikują się przy użyciu portów z zakresu 8000-8003 i portu 9000.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="2ff4b-105">Zapora jest włączona domyślnie i uniemożliwia dostęp do tych portów.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="2ff4b-106">Aby włączyć zaporę dla próbki, wykonaj jedną z następujących procedur, w zależności od wymagań i środowisko zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="2ff4b-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
-   <span data-ttu-id="2ff4b-107">Option 1: Włącz interakcyjne przykładów podczas pracy.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="2ff4b-108">Wprowadzone żadne zmiany zaawansowane konfiguracja zapory i przejdź do rozpocząć tworzenie i uruchamianie przykładów programu.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="2ff4b-109">Po uruchomieniu przykładu **Alert zabezpieczeń Windows** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="2ff4b-110">Z przykładowego program można dodać interaktywnie do listy odblokowane.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="2ff4b-111">Przy użyciu tej procedury trzeba ponownie uruchom przykład.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-111">With this procedure, you may have to then restart the sample.</span></span>  
  
-   <span data-ttu-id="2ff4b-112">Option 2: Włącz przykładowe programy z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="2ff4b-113">Rozpocznij **Panelu sterowania zapory Windows** apletu i Włącz przykładowe programy plan do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="2ff4b-114">Należy najpierw utworzyć programy, dzięki czemu istnieją pliki wykonywalne.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="2ff4b-115">Bardziej szczegółowe instrukcje można znaleźć w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-115">You can find more detailed instructions in the following procedure.</span></span>  
  
-   <span data-ttu-id="2ff4b-116">Opcja 3: Włącz zakres portów z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="2ff4b-117">Rozpocznij **zapory Windows** **Panelu sterowania** apletu i Włącz porty 80, 443, 8000 8003 oraz 9000, które są używane przez próbki.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="2ff4b-118">Bardziej szczegółowe instrukcje można znaleźć w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="2ff4b-119">Ta opcja jest mniej bezpieczna niż inne, ponieważ zezwala ona na dowolnym programowi na używanie tych portów, a nie tylko przykłady.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="2ff4b-120">Jeśli masz pewności, której procedury należy użyć, wybierz opcję pierwszym.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="2ff4b-121">Jeśli korzystasz z zapory, od innego dostawcy, konieczne może wprowadzić zmiany podobne.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2ff4b-122">Zmiana konfiguracji zapory ma wpływ na bezpieczeństwo.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="2ff4b-123">Zaleca się zapisanie zmian upewnij i usuń je, po zakończeniu pracy z przykładów.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="2ff4b-124">Aby włączyć programy przykłady z wyprzedzeniem</span><span class="sxs-lookup"><span data-stu-id="2ff4b-124">To enable samples programs in advance</span></span>  
  
1. <span data-ttu-id="2ff4b-125">Skompiluj przykład.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-125">Build the sample.</span></span>  
  
2. <span data-ttu-id="2ff4b-126">Kliknij przycisk **Start**, kliknij przycisk **Uruchom**i wpisz `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="2ff4b-127">Spowoduje to otwarcie **Panelu sterowania zapory Windows** apletu.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ff4b-128">Musi mieć uprawnienia do zmiany ustawień zapory, aby uruchomić przykłady, które muszą mieć możliwość komunikowania się przez zaporę Windows.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="2ff4b-129">Jeśli niektóre ustawienia zapory są niedostępne, a komputer jest podłączony do domeny, administrator systemu może kontrolowanie tych ustawień za pomocą zasad grupy.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3. <span data-ttu-id="2ff4b-130">Wykonaj jedną z następujących czynności określonego działania umożliwiające programu przez zaporę Windows:</span><span class="sxs-lookup"><span data-stu-id="2ff4b-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    -   <span data-ttu-id="2ff4b-131">Windows 7 lub Windows Server 2008 r2, wybierz polecenie **Zezwalaj programowi lub funkcję przez zaporę Windows**.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="2ff4b-132">Kliknij przycisk **zmiany ustawień**, Zezwalaj na **inny Program...** .</span><span class="sxs-lookup"><span data-stu-id="2ff4b-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    -   <span data-ttu-id="2ff4b-133">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], kliknij przycisk **Zezwól programu przez zaporę Windows**.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-133">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4. <span data-ttu-id="2ff4b-134">Na **wyjątki** kliknij pozycję **Dodaj Program**.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5. <span data-ttu-id="2ff4b-135">Kliknij przycisk **Przeglądaj** i wybierz plik wykonywalny próbki mają być uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6. <span data-ttu-id="2ff4b-136">Powtórz kroki 4 i 5, aż zostaną dodane pliki wykonywalne przykładów, które mają być uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7. <span data-ttu-id="2ff4b-137">Kliknij przycisk **OK** zamknąć aplet Zapora.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="2ff4b-138">Aby włączyć zakres portów z wyprzedzeniem</span><span class="sxs-lookup"><span data-stu-id="2ff4b-138">To enable a port range in advance</span></span>  
  
1. <span data-ttu-id="2ff4b-139">Kliknij przycisk **Start**, kliknij przycisk **Uruchom**i wpisz `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="2ff4b-140">Spowoduje to otwarcie **Panelu sterowania zapory Windows** apletu.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2. <span data-ttu-id="2ff4b-141">Windows 7 lub Windows Server 2008 R2 wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="2ff4b-142">Kliknij przycisk **Zaawansowane ustawienia** w lewej kolumnie okna zapory Windows.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2.  <span data-ttu-id="2ff4b-143">Kliknij przycisk **reguły ruchu przychodzącego** w lewej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3.  <span data-ttu-id="2ff4b-144">Kliknij przycisk **nowe reguły** w prawej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-144">Click **New Rules** in the right column.</span></span>  
  
    4.  <span data-ttu-id="2ff4b-145">Wybierz **portu** i kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-145">Select **Port** and click **next**.</span></span>  
  
    5.  <span data-ttu-id="2ff4b-146">Wybierz **TCP** i wprowadź `8000, 8001, 8002, 8003, 9000, 80, 443` w **określone porty lokalne** pola.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6.  <span data-ttu-id="2ff4b-147">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-147">Click **Next**.</span></span>  
  
    7.  <span data-ttu-id="2ff4b-148">Wybierz **Zezwalaj na połączenie**i kliknij przycisk **dalej** .</span><span class="sxs-lookup"><span data-stu-id="2ff4b-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8.  <span data-ttu-id="2ff4b-149">Wybierz **domeny** i **prywatnej**i kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="2ff4b-150">Nazwa ta reguła `WCF-WF 4.0 Samples`i kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="2ff4b-151">Kliknij przycisk **reguł dla ruchu wychodzącego** i powtórz kroki od c-h.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3. <span data-ttu-id="2ff4b-152">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-152">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1.  <span data-ttu-id="2ff4b-153">Kliknij przycisk **Zezwól programu przez zaporę Windows**.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2.  <span data-ttu-id="2ff4b-154">Na **wyjątki** kliknij pozycję **Dodaj Port**.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3.  <span data-ttu-id="2ff4b-155">Wprowadź nazwę, wprowadź numer portu 8000, a następnie wybierz **TCP** opcji.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4.  <span data-ttu-id="2ff4b-156">Kliknij przycisk **zmiana zakresu** przycisku Wybierz **Moja sieć** jedyną opcją (podsieć), a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5.  <span data-ttu-id="2ff4b-157">Powtórz kroki od b do d dla portów 8001, 8002 8003, 9000, 80 i 443.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4. <span data-ttu-id="2ff4b-158">Kliknij przycisk **OK** zamknąć aplet Zapora.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ff4b-159">Po zakończeniu pracy z próbki, należy usunąć wszelkie wyjątki zapory.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="2ff4b-160">Aby to zrobić, otwórz **Panelu sterowania zapory Windows** apletu i Usuń wszystkie programy lub portu wpisów, które zostały dodane przez poprzedniej procedury.</span><span class="sxs-lookup"><span data-stu-id="2ff4b-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
