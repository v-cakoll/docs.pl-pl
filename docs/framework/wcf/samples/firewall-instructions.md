---
title: Instrukcje dotyczące zapory
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: 5e557963c415cf39c4f25b4854c9863652201146
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961405"
---
# <a name="firewall-instructions"></a><span data-ttu-id="5a24e-102">Instrukcje dotyczące zapory</span><span class="sxs-lookup"><span data-stu-id="5a24e-102">Firewall Instructions</span></span>
<span data-ttu-id="5a24e-103">Należy włączyć kilka portów lub programów w zaporze, aby umożliwić działanie przykładów Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5a24e-103">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="5a24e-104">Wiele przykładów komunikuje się za pomocą portów z zakresu 8000-8003 i portu 9000.</span><span class="sxs-lookup"><span data-stu-id="5a24e-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="5a24e-105">Zapora jest domyślnie włączona i uniemożliwia dostęp do tych portów.</span><span class="sxs-lookup"><span data-stu-id="5a24e-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="5a24e-106">Aby włączyć zaporę dla przykładów, wykonaj jedną z następujących procedur, w zależności od wymagań i środowiska zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="5a24e-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
- <span data-ttu-id="5a24e-107">Option 1: Interaktywnie Włącz próbki w trakcie działania.</span><span class="sxs-lookup"><span data-stu-id="5a24e-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="5a24e-108">Nie wprowadzaj żadnych zmian w konfiguracji zapory i Kontynuuj, aby rozpocząć Kompilowanie i uruchamianie przykładów.</span><span class="sxs-lookup"><span data-stu-id="5a24e-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="5a24e-109">Po uruchomieniu przykładu zostanie wyświetlone okno dialogowe **alert zabezpieczeń systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="5a24e-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="5a24e-110">Przykładowy program można następnie dodać interaktywnie do listy odblokowanej.</span><span class="sxs-lookup"><span data-stu-id="5a24e-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="5a24e-111">Korzystając z tej procedury, może być konieczne ponowne uruchomienie przykładu.</span><span class="sxs-lookup"><span data-stu-id="5a24e-111">With this procedure, you may have to then restart the sample.</span></span>  
  
- <span data-ttu-id="5a24e-112">Opcja 2: Włącz z wyprzedzeniem przykładowe programy.</span><span class="sxs-lookup"><span data-stu-id="5a24e-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="5a24e-113">Uruchom aplet **Panelu sterowania Zapory systemu Windows** i Włącz przykładowe programy, które zamierzasz uruchomić.</span><span class="sxs-lookup"><span data-stu-id="5a24e-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="5a24e-114">Musisz najpierw skompilować programy, aby pliki wykonywalne istniały.</span><span class="sxs-lookup"><span data-stu-id="5a24e-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="5a24e-115">Bardziej szczegółowe instrukcje można znaleźć w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="5a24e-115">You can find more detailed instructions in the following procedure.</span></span>  
  
- <span data-ttu-id="5a24e-116">Opcja 3: Włącz z wyprzedzeniem zakres portów.</span><span class="sxs-lookup"><span data-stu-id="5a24e-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="5a24e-117">Uruchom aplet **Panelu sterowania** **zapory systemu Windows** i włącz porty 80, 443, 8000-8003 i 9000, które są używane przez przykłady.</span><span class="sxs-lookup"><span data-stu-id="5a24e-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="5a24e-118">Bardziej szczegółowe instrukcje można znaleźć w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="5a24e-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="5a24e-119">Ta opcja jest mniej bezpieczna niż w przypadku innych, ponieważ umożliwia każdemu programowi korzystanie z tych portów, a nie tylko przykładów.</span><span class="sxs-lookup"><span data-stu-id="5a24e-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="5a24e-120">Jeśli nie masz pewności, której procedury użyć, wybierz pierwszą opcję.</span><span class="sxs-lookup"><span data-stu-id="5a24e-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="5a24e-121">Jeśli używasz zapory od innego dostawcy, może być konieczne wprowadzenie podobnych zmian.</span><span class="sxs-lookup"><span data-stu-id="5a24e-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5a24e-122">Zmiana konfiguracji zapory wpływa na bezpieczeństwo.</span><span class="sxs-lookup"><span data-stu-id="5a24e-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="5a24e-123">Zalecamy zapisanie wprowadzonych zmian i ich usunięcie po zakończeniu pracy z przykładami.</span><span class="sxs-lookup"><span data-stu-id="5a24e-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="5a24e-124">Aby włączyć z wyprzedzeniem programy próbne</span><span class="sxs-lookup"><span data-stu-id="5a24e-124">To enable samples programs in advance</span></span>  
  
1. <span data-ttu-id="5a24e-125">Kompiluj przykład.</span><span class="sxs-lookup"><span data-stu-id="5a24e-125">Build the sample.</span></span>  
  
2. <span data-ttu-id="5a24e-126">Kliknij przycisk **Start**, kliknij pozycję **Uruchom**, `firewall.cpl`a następnie wpisz polecenie.</span><span class="sxs-lookup"><span data-stu-id="5a24e-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="5a24e-127">Spowoduje to otwarcie apletu **Panelu sterowania Zapory systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="5a24e-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a24e-128">Musisz mieć uprawnienia do zmiany ustawień zapory, aby uruchamiać próbki, które wymagają możliwości komunikowania się przez zaporę systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5a24e-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="5a24e-129">Jeśli niektóre ustawienia zapory są niedostępne, a komputer jest połączony z domeną, administrator systemu może kontrolować te ustawienia za pomocą zasady grupy.</span><span class="sxs-lookup"><span data-stu-id="5a24e-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3. <span data-ttu-id="5a24e-130">Wykonaj jedną z następujących czynności, aby umożliwić programowi za pomocą zapory systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="5a24e-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    - <span data-ttu-id="5a24e-131">W systemie Windows 7 lub Windows Server 2008 R2 kliknij opcję **Zezwól programowi lub funkcji za pomocą zapory systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="5a24e-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="5a24e-132">Kliknij pozycję **Zmień ustawienia**, Zezwól na **inny program...** .</span><span class="sxs-lookup"><span data-stu-id="5a24e-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    - <span data-ttu-id="5a24e-133">W [!INCLUDE[wv](../../../../includes/wv-md.md)] systemie [!INCLUDE[lserver](../../../../includes/lserver-md.md)]lub kliknij opcję **Zezwól programowi na korzystanie z zapory systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="5a24e-133">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4. <span data-ttu-id="5a24e-134">Na karcie **wyjątki** kliknij pozycję **Dodaj program**.</span><span class="sxs-lookup"><span data-stu-id="5a24e-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5. <span data-ttu-id="5a24e-135">Kliknij przycisk **Przeglądaj** i wybierz plik wykonywalny przykładu, który ma zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5a24e-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6. <span data-ttu-id="5a24e-136">Powtórz kroki 4 i 5, dopóki nie dodasz plików wykonywalnych ze wszystkich przykładów, które planujesz uruchomić.</span><span class="sxs-lookup"><span data-stu-id="5a24e-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7. <span data-ttu-id="5a24e-137">Kliknij przycisk **OK** , aby zamknąć aplet Zapora.</span><span class="sxs-lookup"><span data-stu-id="5a24e-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="5a24e-138">Aby włączyć z wyprzedzeniem zakres portów</span><span class="sxs-lookup"><span data-stu-id="5a24e-138">To enable a port range in advance</span></span>  
  
1. <span data-ttu-id="5a24e-139">Kliknij przycisk **Start**, kliknij pozycję **Uruchom**, `firewall.cpl`a następnie wpisz polecenie.</span><span class="sxs-lookup"><span data-stu-id="5a24e-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="5a24e-140">Spowoduje to otwarcie apletu **Panelu sterowania Zapory systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="5a24e-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2. <span data-ttu-id="5a24e-141">W systemie Windows 7 lub Windows Server 2008 R2 wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="5a24e-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1. <span data-ttu-id="5a24e-142">Kliknij pozycję **Ustawienia zaawansowane** w lewej kolumnie okna Zapora systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5a24e-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2. <span data-ttu-id="5a24e-143">W lewej kolumnie kliknij pozycję **reguły ruchu przychodzącego** .</span><span class="sxs-lookup"><span data-stu-id="5a24e-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3. <span data-ttu-id="5a24e-144">Kliknij pozycję **nowe reguły** w prawej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="5a24e-144">Click **New Rules** in the right column.</span></span>  
  
    4. <span data-ttu-id="5a24e-145">Wybierz pozycję **port** , a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="5a24e-145">Select **Port** and click **next**.</span></span>  
  
    5. <span data-ttu-id="5a24e-146">Wybierz opcję **TCP** i `8000, 8001, 8002, 8003, 9000, 80, 443` wprowadź w polu **określone porty lokalne** .</span><span class="sxs-lookup"><span data-stu-id="5a24e-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6. <span data-ttu-id="5a24e-147">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="5a24e-147">Click **Next**.</span></span>  
  
    7. <span data-ttu-id="5a24e-148">Wybierz opcję **Zezwalaj na połączenie**, a następnie kliknij przycisk **dalej** .</span><span class="sxs-lookup"><span data-stu-id="5a24e-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8. <span data-ttu-id="5a24e-149">Wybierz pozycję **domena** i **prywatny**, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="5a24e-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="5a24e-150">Nadaj nazwę regule `WCF-WF 4.0 Samples`i kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="5a24e-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="5a24e-151">Kliknij pozycję **reguły ruchu** wychodzącego i powtórz kroki od c do h.</span><span class="sxs-lookup"><span data-stu-id="5a24e-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3. <span data-ttu-id="5a24e-152">W [!INCLUDE[wv](../../../../includes/wv-md.md)] systemie [!INCLUDE[lserver](../../../../includes/lserver-md.md)]lub wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="5a24e-152">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1. <span data-ttu-id="5a24e-153">Kliknij pozycję **Zezwól programowi przez zaporę systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="5a24e-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2. <span data-ttu-id="5a24e-154">Na karcie **wyjątki** kliknij pozycję **Dodaj port**.</span><span class="sxs-lookup"><span data-stu-id="5a24e-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3. <span data-ttu-id="5a24e-155">Wprowadź nazwę, wprowadź 8000 jako numer portu, a następnie wybierz opcję **TCP** .</span><span class="sxs-lookup"><span data-stu-id="5a24e-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4. <span data-ttu-id="5a24e-156">Kliknij przycisk **Zmień zakres** , wybierz opcję tylko **moja sieć** (podsieć), a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5a24e-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5. <span data-ttu-id="5a24e-157">Powtórz kroki od b do d dla portów 8001, 8002, 8003, 9000, 80 i 443.</span><span class="sxs-lookup"><span data-stu-id="5a24e-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4. <span data-ttu-id="5a24e-158">Kliknij przycisk **OK** , aby zamknąć aplet Zapora.</span><span class="sxs-lookup"><span data-stu-id="5a24e-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a24e-159">Usuń wszystkie wyjątki zapory po zakończeniu pracy z przykładami.</span><span class="sxs-lookup"><span data-stu-id="5a24e-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="5a24e-160">W tym celu należy otworzyć aplet **Panelu sterowania Zapory systemu Windows** i usunąć wszystkie programy lub wpisy portów, które zostały dodane przez poprzednie procedury.</span><span class="sxs-lookup"><span data-stu-id="5a24e-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
