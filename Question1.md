### The 1990 AT&T Network Collapse :

Bloquant 



Il s'agit d'un bug global parce qu'il y a eu une mauvaise gestion de la concurrence

Before this collapse, AT&T's long-distance network was accepted as  reliable and strong. It was carrying over 70% of the nation's  long-distance traffic and routing over 115 million telephone calls. This collapse resulted in a $60 million lost as of 75 million missed phone  by AT&T customers calls and 200 000 airline and hotel reservations  and other businesses that relied on the telephone network.



The bug occurred because of a break statement in an if  clause nested in a switch clause in the upgraded recovery software of  all switches. All the switches became unreliable at the same time while  each switch tries to determine if the neighbor switches were reliable or not.

```
1  while (ring receive buffer not empty  and side buffer not empty) DO
2    Initialize pointer to first message in side buffer or ring receive buffer
3    get copy of buffer
4    switch (message)
5       case (incoming_message):
6             if (sending switch is out of service) DO
7                 if (ring write buffer is empty) DO
8                     send "in service" to status map
9                 else
10                    break
11            END IF
12            process incoming message, set up pointers to optional parameters
13            break
14      END SWITCH
15   do optional parameter work
```

When the destination switch received the second of the two closely timed messages while it was still busy with the first (buffer not empty, line 7), the program should have dropped out of the `if` clause  (line 7), processed the incoming message, and set up the pointers to the database (line 11). Instead, because of the break statement in the `else` clause (line 10), the program dropped out of the case statement  entirely and began doing optional parameter work which overwrote the  data (line 13). Error correction software detected the overwrite and  shut the switch down while it couls reset. Because every switch  contained the same software, the resets cascaded down the network,  incapacitating the system.



ça aurait pu être testé s'ils avaient fait des tests de résiliences ( plusieurs appel à la suite sur une courte durée)



# 2

Il s'agit d'un bug local dans une classe de test. Il s'agit d'un test sur un iterator

il s'agit d'un bug local du au trop grand nombre de iterator.next() sur la list, ils ont donc removela mauvaise partie et tester l'ensemble des classes associées. Ils n'ont pas d'ajouter de nouveau test puisqu'il s'agissait d'une erreur dans une classe de test mais ils ont bien vérifié les classes de test.

https://issues.apache.org/jira/projects/COLLECTIONS/issues/COLLECTIONS-802?filter=doneissues

# 3 

Concrete experiments : 

- terminate virtual machine instances
-  inject latency into requests between services
-  fail requests between services
-  fail an internal service

Based on the principles, define an experiment:

1. Start by defining ‘steady state’ as some measurable output of a system that indicates

normal behavior.

2. Hypothesize that this steady state will continue in both the control group and the

experimental group.

3. Introduce variables that reflect real world events like servers that crash, hard drives that

malfunction, network connections that are severed.

4. Try to disprove the hypothesis by looking for a difference in steady state between the

control group and the experimental group	



D'autres entreprises utilise le Chaos Engeniring : Amazon et Windows. Pour le service AWS, ils peuvent faire crasher des serveurs et voir comment rediriger les demandes et voir si des serveurs de sauvegarde sont utilisés. Pour windows, ils peuvent introduire des erreurs de mémoire par erreur et tester la résilience du programme. Est ce que l'erreur va bloquer tout le programme et du coup va pousser windows a le recharger ou le programme va tout simplement planter. 

# 4 

Sur le papier, il semble qu'une spécification formelle prouvant la gestion des erreurs pousserait à moins tester les implémentations du code. Par exemple avec des sécurités sur la taille des entiers, gestions des erreurs et gestion de la concurrence. Donc théoriquement cela pousse à produire moins de test puisque c'est prouvé.

# 5 


We have presented a full mechanisation of the core Web-
Assembly language, together with several proofs of sound	
ness, and verified implementations of a type checker and
interpreter. In the course of conducting these proofs, we have
identified and assisted in fixing several errors in the official
WebAssembly specification.