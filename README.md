# DALORADIUS CANT DISABLED USER PPP/TUNNEL

I get some problems when using daloradius + freeradius auth for ppp/tunnel on proxy. I want users who cannot be used to be disabled, so that they cannot be used again. However, when using the disable feature from daloradius, the user cannot be disabled and can still auth/login.

It turns out that daloradius disables users by creating a new group with the name "daloRADIUS-Disabled-Users". The group cannot disable users properly. So I searched for documentation related to disable users in freeradius 3.2 and it turns out that freeradius requires the "Fall-Through" attribute with the value "Yes" to disable users. 

So I slightly reconfigured the Daloradius source code so that when the disable button is clicked, it will enter the "Fall-Through" attribute into the user to be disabled.

File with name mng-list-all.php and user_actions.php that's all the files I edited