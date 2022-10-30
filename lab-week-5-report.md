# Lab-week-5-report
## Introduction
*Hello! Welcome to this week's lab report. In this lab report, you will learn various uses of the "grep" command through three examples!*

## Part 1: The "-c" command
When you are reading and want to search for useful documentations to support your analysis, you may want to find useful documents faster when you get them. So by using the "-c" option, you can get an idea of does the document contains the word you want, and by how many.

Input1:
```
grep -c "Tuesday" chapter-1.txt
```
Output1:
```
3
```
> By using the command "-c", we can know how many lines matches the pattern we have chosen, which is "Tuesday". This option is pretty useful, because it is always important for people to know the frequency of certain words/pattern's occurence in a file;in this case, Tuesday is the date of the 911, so if a file includes many Tuesday, it may be talking about what happened on that day. So people can quickly understand if their desired "key word" is in this file or not, which could help people to make decision on continue reading the file or not.

Input2:
```
grep -c "studies" 1468-6708-3-1.txt
```
Output2:
```
10
```
> By using the command "-c", people can have an idea of how many times their interested word occurs in the document. In this case, we are searching in the biomed category, so this implies that in this document, the author mentioned studies at least 10 times, so they maybe talking about studies they have done and people who are interested in that can continue reading.

Input3:
```
grep -c "goal" commission_report.txt
```
Output3:
```
2
```
> By using the command "-c", we can know how many lines matches the pattern we have chosen, which is "goal". Based on the observation, we can see that there are only 2 lines that has our targeted word goal. Therefore, people can infer that since the frequency for "goal" is not that high in this document, so maybe the author did not cover the goal of their commission in this report, or only briefly talked about that,

## Part 2: "-n" command
As we may wonder, after I know I want to keep reading the file and know there are a lot of my intersted words in the file, how can I know better and more on what are their contents? Since we were merely making guesses when using the "-c" option in the previous part.

Input1:
```
grep -n "studies" 1468-6708-3-1.txt
```
Output1:
```
9:        Six large controlled population-based studies of
12:        for relevant covariates [ 1 2 3 4 5 6 ] . All studies found
15:        in certain small subsets. A review of 13 studies of older
23:        number of studies of older persons is fairly small, and
24:        because few studies have examined the relation of BMI to
73:          was associated with lower survival in studies cited
87:          of health events in many studies [ 17 ] . Because we are
130:          related to mortality and morbidity in previous studies,
316:          Recent studies have defined obesity without reference
388:          results from many studies. However, health measures
```
> Now we can sort of zoom in to those words and explore whether these information are important for us or not, and it can also let us know where each line is in the file. For example, if I am interested in finding "population-based" studies, I cansee that it is in the 9th line of this document.

Input2:
```
grep -n "CIA" chapter-10.txt
```
Output2:
```
331:                proposed inserting CIA teams into Afghanistan to work with Afghan warlords who would
332:                join the fight against al Qaeda.46These CIA teams would act jointly with the
360:                the CIA.
487:                1995 Manila air plot in crashing an explosives-laden plane into CIA headquarters,
562:                    Qaeda and Taliban targets. In an innovative joint effort, CIA and Special
588:            Within about two months of the start of combat operations, several hundred CIA
595:                According to a senior CIA officer who helped devise the overall strategy, the CIA
```
> Here, we can see that if we are interested in the activities of the CIA during the 911 attack, the "-n" option is able to bring us all the line number and line contents about the CIA in the chapter-10.txt file. For example, If I want to know what the senior CIA officier said, I would start reading from line 595 to quickly navigate to the part of the file that is important for me.

Input3:
```
grep -n "risk" Session3-PDF.txt
```
Output3:
```
19:admission, and the fact that alcohol is a risk factor both for the
145:consumption. These interventions appeared to affect risk taking in
206:risk and re-injury.
225:risky behaviors.20,32,33 One recent study demonstrated that a
229:male and female high-risk drinkers.34 Based on these interventions
248:the important outcome. Change of drinking and risky behaviors is
292:drinking behavior and/or reduce risk of re-injury. The number of
295:range from minimal to very sizeable reduction in risks that have
303:terms of reductions in drinking and of risk profiles. Motivational
305:important clinical outcomes in terms of risk-taking, negative
389:settings to reduce drinking and alcohol related risks. The first
617:trauma center as a means of reducing the risk of injury
688:physician and nurse practitioner-delivered counseling for high risk
826:the at-risk, harmful, or hazardous drinker; or the dependent
990:with ED patients at risk for and currently experiencing problem
1004:in the ED for persons who are at-risk drinkers, problem drinkers,
1019:studies. In addition, the target of the intervention (at-risk
1044:moment may be effective for non-injured persons who drink at risk
1064:alcohol consumption of at-risk drinkers and the limited time for
1076:positive for at-risk drinking or more serious alcohol-related
1079:system of care for patients with at-risk and problem drinking
1107:multiple health risks (e.g., smoking, alcohol use, seat belt use),
1140:4. Cherpitel CJ. Alcohol, Injury, and risk-taking behavior:
1190:risk of injury recurrance. Ann Surg 1999;230:473-83.
1198:19. Blow FC, Barry KL. Older Patients with at-risk and problem
1288:study of adolescents found reductions in risky behavior and
1600:at behavioral risk factors might get us a more prominent place on
1603:three risk factors that often overlap in these populations. If the
1610:positive for one risk factor often have multiple risk factors. The
1611:patient could decide how many risk factors could be addressed at
1636:there were so many risk factors that should be addressed that some
1638:of alcohol problems was higher than other risk factors. Physicians
```
> Similarly, it would be helpful to get a direction of where to go(line numbers) and a brief introduction of what the contents are(matched line contents) when people are reading. In this case, I would like to see what are some risks related to alcohols, so that I can start by using the "-n" command to filter those lines that are not important for us and only keep useful lines. 

## Part 3: "-A n" command
However, by seeing one line of the matched string/pattern may not give us enough useful information, so let us use a more detailed way to provide a more sophisticated information of the key-word we would like to search in the document.

Input1:
```
grep -A 3 "White House" chapter-10.txt
```
Output1:
```
White House Situation Room that morning.
            
            While the plan at the elementary school had been to return to Washington, by the time
                Air Force One was airborne at 9:55 A.M. the Secret Service, the President's
--
                been implemented. 9 The Pentagon had been struck; the White House or the Capitol had
                narrowly escaped direct attack. Extraordinary security precautions were put in place
                at the nation's borders and ports.
            In the late afternoon, the President overruled his aides' continuing reluctance to
--
                Base. He was flown by helicopter back to the White House, passing over the
                still-smoldering Pentagon. At 8:30 that evening, President Bush addressed the nation
                from the White House. After emphasizing that the first priority was to help the
                injured and protect against any further attacks, he said: "We will make no
                distinction between the terrorists who committed these acts and those who harbor
                them." He quoted Psalm 23-"though I walk through the valley of the shadow of death .
--
            As the urgent domestic issues accumulated, White House Deputy Chief of Staff Joshua
                Bolten chaired a temporary "domestic consequences" group.
            
            The agenda in those first days is worth noting, partly as a checklist for future
--
                    involving the White House, the Treasury Department, and the Securities and
                    Exchange Commission, aided by unprecedented cooperation among the usually
                    competitive firms of the financial industry, the markets reopened on Monday,
                    September 17.
--
                Cheney had decided to recommend, at least as a first step, a new White House entity
                to coordinate all the relevant agencies rather than tackle the challenge of
                combining them in a new department. This new White House entity would be a homeland
                security adviser and Homeland Security Council-paralleling the National Security
                Council system. Vice President Cheney reviewed the proposal with President Bush and
                other advisers. President Bush announced the new post and its first occupant-
--
                anyone at the White House above the level of Richard Clarke participated in a
                decision on the departure of Saudi nationals. The issue came up in one of the many
                video teleconferences of the interagency group Clarke chaired, and Clarke said he
                approved of how the FBI was dealing with the matter when it came up for interagency
--
                anybody at the White House."
            
            Although White House Chief of Staff Andrew Card remembered someone telling him about
                the Saudi request shortly after 9/11, he said he had not talked to the Saudis and
                did not ask anyone to do anything about it. The President and Vice President told us
                they were not aware of the issue at all until it surfaced much later in the media.
--
                Director Robert Mueller. From the White House staff, National Security Advisor
                Condoleezza Rice and Chief of Staff Card were part of the core group, often joined
                by their deputies, Stephen Hadley and Joshua Bolten.
            In this restricted National Security Council meeting, the President said it was a
--
                to the White House a paper titled "Game Plan for a Political- Military Strategy for
                Pakistan and Afghanistan." The paper took it as a given that Bin Ladin would
                continue to act against the United States even while under Taliban control. It
                therefore detailed specific U.S. demands for the Taliban: surrender Bin Ladin and
```
> Surprisingly, by using the "-A n" command, we obtain the contents of n lines after the matched line, and if one of the lines in the following n lines also contains the key word we are searching for, this command will also display n lines after that line. Therefore, we are able to extract key informatio nfaster through this way, as we know that if we only have one line, it may not contain enough informatio nwe want to read.

Input2:
```
grep -A 3 "protein" rr196.txt
```
Output2:
```
protein-determined fiber type closely mirrorred the PCR
          results at the mRNA level. Table 2demonstrates that, as
          determined by immunocytochemistry, emphysematous animals
          had a significantly lower percentage of fibers classified
--
        represent 6.1% of all MHC protein in young rat diaphragm,
        and their IId/IIx result of 44.9% is also quite different
        from our PCR result, while their I and IIa findings are
        very similar to our PCR results, and their IId/IIx result
--
        more IId protein by electrophoresis in 5-month-old rats [
        29 ] .
        The differences between the findings of these reports
        and ours might at first glance result from the age of the
--
        protein levels; and similarly between techniques measuring
        protein by gel and those measuring protein by
        immunocytochemistry.
        Although increased activities of citrate synthase [ 7 ]
        and SDH [ 2 3 ] have usually been demonstrated in the
--
        emphysematous rat diaphragm at both the protein and mRNA
        levels. Although this shift toward a slower isoform is not
        as marked as that reported in humans [ 12 13 ] , in which
        MHC type I is upregulated and both IIa and IIx are
--
        endurance swimming, IIb protein from costal diaphragm of
        rats fell by 54%, also without statistically significant
        changes in the amounts of other MHC isoforms. This suggests
        that the effects of emphysema on the diaphragm are, as has
--
        proteins in these animals, because these proteins are
        responsible for a significant fraction of energy
        consumption in skeletal muscle, second only to the energy
        consumed by the ATPase responsible for movement of the
--
        IIb MHC expression at both the protein and mRNA levels in
        the diaphragmatic muscle of rats with elastase-induced
        emphysema. In concert with this shift away from the fastest
        MHC isoform, we have demonstrated 'slower' physiological
```
Here, by using the "-A n" command, we have collected all the quotes and information about how proteins was analyzed in the study. As we can see, each of these separated paragraphs gives us what the role of protein is and we can quickly read through to find the part that we are interested in, or find it first and then change the "n" part of the "-A n" command to expand to more information.

Input3:
```
grep -A 3 "increase" water_fees.txt
```
Output3:
```
jasondai@Jasons-MacBook-Air Media % grep -A 3 "increase" water_fees.txt
It's either a big increase or a loss of service for the Tulare
County town.
By Joan Obra
Alpaugh residents may see their water fees triple to avoid
--
president Steve Martin. The district, which didn't increase prices
fast enough to meet the rising cost of delivering water, amassed an
estimated $330,000 power bill during the state energy crisis. Last
month, Alpaugh Irrigation customers approved a monthly fee increase
from $20 to $68.
If Tulare County Water Works wants to keep its 170 hookups
flowing, Martin said, it must also raise rates.
--
election. The propertyrelated fee increase requires voter approval
under Proposition 218, a process Tulare County Water Works
officials started after they learned the outcome of Alpaugh
Irrigation's vote.
--
leaders will explain the rules. To block the possible fee increase,
51% of property owners in the district must submit protest votes in
writing. No protest vote means approval of the price jump.
But misinformation already is rampant. Sandra Meraz, Tulare
```
Magically, the "-A n" option brings us many separated paragraphs that contains the following n lines of contents we are interested in. In this demonstration, I want to see what are some increases in the water fee document, such as the cost of delivering water's increase, or people's unstatisfactory to the increase of water fee, which is convinient to read, because each paragraph is clearly separated and the size of each paragraph is under our control.

## Conclusion
*All in all, by walking through this lab-report, we can know that grep is an useful and interesting option, and adding options to the grep command, we can make it become even more interesting and useful.
