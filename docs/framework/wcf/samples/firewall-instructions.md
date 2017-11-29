---
title: "Instrukcje dotyczące zapory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
caps.latest.revision: "32"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0aac3a161b0482bad1a32f5223d2031402a632cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="firewall-instructions"></a><span data-ttu-id="20dde-102">Instrukcje dotyczące zapory</span><span class="sxs-lookup"><span data-stu-id="20dde-102">Firewall Instructions</span></span>
<span data-ttu-id="20dde-103">Należy włączyć kilka portów lub programów w zaporze, tak że [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] próbki mogą działać.</span><span class="sxs-lookup"><span data-stu-id="20dde-103">You must enable several ports or programs in the firewall so that the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples can function.</span></span> <span data-ttu-id="20dde-104">Wiele próbek komunikują się przy użyciu portów w zakresie 8000-8003 i portu 9000.</span><span class="sxs-lookup"><span data-stu-id="20dde-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="20dde-105">Zapora jest włączona domyślnie i uniemożliwia dostęp do tych portów.</span><span class="sxs-lookup"><span data-stu-id="20dde-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="20dde-106">Aby włączyć zapory próbek, wykonaj jedną z następujących procedur, w zależności od wymagań i środowisko zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="20dde-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
-   <span data-ttu-id="20dde-107">Opcja 1: Włącz interakcyjne przykłady podczas pracy.</span><span class="sxs-lookup"><span data-stu-id="20dde-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="20dde-108">Nie wprowadzisz wcześniejszym zmian do konfiguracji zapory i przejdź do zacząć tworzyć i uruchamiać próbek.</span><span class="sxs-lookup"><span data-stu-id="20dde-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="20dde-109">Po uruchomieniu próbkę **Alert zabezpieczeń systemu Windows** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="20dde-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="20dde-110">Przykładowy program zagrożona można dodać interaktywnie do listy odblokowany.</span><span class="sxs-lookup"><span data-stu-id="20dde-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="20dde-111">Ta procedura może być ponowne uruchomienie przykładu.</span><span class="sxs-lookup"><span data-stu-id="20dde-111">With this procedure, you may have to then restart the sample.</span></span>  
  
-   <span data-ttu-id="20dde-112">Opcja 2: Włączanie przykładowe programy z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="20dde-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="20dde-113">Uruchom **Panelu sterowania Zapory systemu Windows** apletu i włączyć plan do uruchamiania programów próbki.</span><span class="sxs-lookup"><span data-stu-id="20dde-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="20dde-114">Programy należy utworzyć najpierw, więc istnieje plików wykonywalnych.</span><span class="sxs-lookup"><span data-stu-id="20dde-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="20dde-115">Bardziej szczegółowe instrukcje można znaleźć w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="20dde-115">You can find more detailed instructions in the following procedure.</span></span>  
  
-   <span data-ttu-id="20dde-116">Opcja 3: Włącz zakres portów z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="20dde-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="20dde-117">Uruchom **zapory systemu Windows** **Panelu sterowania** apletu i Włącz porty 80, 443, 8000 8003 i 9000, które są używane przez próbek.</span><span class="sxs-lookup"><span data-stu-id="20dde-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="20dde-118">Bardziej szczegółowe instrukcje można znaleźć w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="20dde-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="20dde-119">Ta opcja jest mniej bezpieczne od innych, ponieważ zezwala ona na dowolnym programem na te porty, nie tylko próbek.</span><span class="sxs-lookup"><span data-stu-id="20dde-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="20dde-120">Masz pewności, procedurę do użycia, jeśli pierwsza opcja.</span><span class="sxs-lookup"><span data-stu-id="20dde-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="20dde-121">Jeśli korzystasz z zapory od innego dostawcy, konieczne może być podobne zmiany.</span><span class="sxs-lookup"><span data-stu-id="20dde-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20dde-122">Zmiana konfiguracji zapory ma wpływ na bezpieczeństwo.</span><span class="sxs-lookup"><span data-stu-id="20dde-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="20dde-123">Zalecane jest zapisanie zmian należy i usuń je po zakończeniu pracy z próbek.</span><span class="sxs-lookup"><span data-stu-id="20dde-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="20dde-124">Aby włączyć programy próbki z wyprzedzeniem</span><span class="sxs-lookup"><span data-stu-id="20dde-124">To enable samples programs in advance</span></span>  
  
1.  <span data-ttu-id="20dde-125">Tworzenie przykładowej.</span><span class="sxs-lookup"><span data-stu-id="20dde-125">Build the sample.</span></span>  
  
2.  <span data-ttu-id="20dde-126">Kliknij przycisk **Start**, kliknij przycisk **Uruchom**i wpisz `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="20dde-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="20dde-127">Spowoduje to otwarcie **Panelu sterowania Zapory systemu Windows** apletu.</span><span class="sxs-lookup"><span data-stu-id="20dde-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20dde-128">Musi mieć uprawnienia do zmiany ustawień zapory, aby uruchomić przykłady, które muszą mieć możliwość komunikacji za pośrednictwem zapory systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="20dde-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="20dde-129">Jeśli niektóre ustawienia zapory są niedostępne, a komputer jest podłączony do domeny, administrator systemu może kontroluje te ustawienia za pomocą zasad grupy.</span><span class="sxs-lookup"><span data-stu-id="20dde-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3.  <span data-ttu-id="20dde-130">Wykonaj jedną z następujących kroków określonego działania umożliwia programu przez zaporę systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="20dde-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    -   <span data-ttu-id="20dde-131">W systemie Windows 7 lub Windows Server 2008 r2, kliknij polecenie **Zezwalaj programowi lub funkcji przez zaporę systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="20dde-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="20dde-132">Kliknij przycisk **zmienić ustawienia**, Zezwalaj **inny Program...** .</span><span class="sxs-lookup"><span data-stu-id="20dde-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    -   <span data-ttu-id="20dde-133">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], kliknij przycisk **Zezwól programu przez zaporę systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="20dde-133">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4.  <span data-ttu-id="20dde-134">Na **wyjątki** , kliknij pozycję **Dodaj Program**.</span><span class="sxs-lookup"><span data-stu-id="20dde-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5.  <span data-ttu-id="20dde-135">Kliknij przycisk **Przeglądaj** i wybrać plik wykonywalny próbki ma zostać uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="20dde-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6.  <span data-ttu-id="20dde-136">Powtórz kroki 4 i 5, aż zostaną dodane pliki wykonywalne próbek, który ma zostać uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="20dde-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7.  <span data-ttu-id="20dde-137">Kliknij przycisk **OK** zamknąć aplet zapory.</span><span class="sxs-lookup"><span data-stu-id="20dde-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="20dde-138">Aby włączyć zakres portów z wyprzedzeniem</span><span class="sxs-lookup"><span data-stu-id="20dde-138">To enable a port range in advance</span></span>  
  
1.  <span data-ttu-id="20dde-139">Kliknij przycisk **Start**, kliknij przycisk **Uruchom**i wpisz `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="20dde-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="20dde-140">Spowoduje to otwarcie **Panelu sterowania Zapory systemu Windows** apletu.</span><span class="sxs-lookup"><span data-stu-id="20dde-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2.  <span data-ttu-id="20dde-141">W systemie Windows 7 lub Windows Server 2008 R2 wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="20dde-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="20dde-142">Kliknij przycisk **Zaawansowane ustawienia** w lewej kolumnie okna zapory systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="20dde-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2.  <span data-ttu-id="20dde-143">Kliknij przycisk **reguły ruchu przychodzącego** w lewej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="20dde-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3.  <span data-ttu-id="20dde-144">Kliknij przycisk **nowe reguły** w prawej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="20dde-144">Click **New Rules** in the right column.</span></span>  
  
    4.  <span data-ttu-id="20dde-145">Wybierz **portu** i kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="20dde-145">Select **Port** and click **next**.</span></span>  
  
    5.  <span data-ttu-id="20dde-146">Wybierz **TCP** , a następnie wprowadź `8000, 8001, 8002, 8003, 9000, 80, 443` w **określone porty lokalne** pola.</span><span class="sxs-lookup"><span data-stu-id="20dde-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6.  <span data-ttu-id="20dde-147">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="20dde-147">Click **Next**.</span></span>  
  
    7.  <span data-ttu-id="20dde-148">Wybierz **zezwalały na połączenie**i kliknij przycisk **dalej** .</span><span class="sxs-lookup"><span data-stu-id="20dde-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8.  <span data-ttu-id="20dde-149">Wybierz **domeny** i **prywatnej**i kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="20dde-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="20dde-150">Nazwę tej reguły `WCF-WF 4.0 Samples`i kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="20dde-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="20dde-151">Kliknij przycisk **reguły wychodzące** i powtórz kroki od c-h.</span><span class="sxs-lookup"><span data-stu-id="20dde-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3.  <span data-ttu-id="20dde-152">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="20dde-152">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1.  <span data-ttu-id="20dde-153">Kliknij przycisk **Zezwól programu przez zaporę systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="20dde-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2.  <span data-ttu-id="20dde-154">Na **wyjątki** , kliknij pozycję **Dodaj Port**.</span><span class="sxs-lookup"><span data-stu-id="20dde-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3.  <span data-ttu-id="20dde-155">Wprowadź nazwę, wprowadź 8000 jako numer portu, a następnie wybierz **TCP** opcji.</span><span class="sxs-lookup"><span data-stu-id="20dde-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4.  <span data-ttu-id="20dde-156">Kliknij przycisk **Zmień zakres** przycisku Wybierz **Moja sieć** tylko opcja (podsieć), a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="20dde-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5.  <span data-ttu-id="20dde-157">Powtórz kroki od b-d dla portów 8001, 8002, 8003 9000, 80 i 443.</span><span class="sxs-lookup"><span data-stu-id="20dde-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4.  <span data-ttu-id="20dde-158">Kliknij przycisk **OK** zamknąć aplet zapory.</span><span class="sxs-lookup"><span data-stu-id="20dde-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20dde-159">Po zakończeniu pracy z próbki, należy usunąć wszelkie wyjątki zapory.</span><span class="sxs-lookup"><span data-stu-id="20dde-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="20dde-160">Aby to zrobić, otwórz **Panelu sterowania Zapory systemu Windows** apletu i Usuń wszystkie programy lub portu wpisów, które zostały dodane w ramach poprzednich procedur.</span><span class="sxs-lookup"><span data-stu-id="20dde-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
